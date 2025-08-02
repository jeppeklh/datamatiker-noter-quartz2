tags: #SQL #Programmering #SQLSecurity #SQLInjection

> [!tldr] Definition
> SQL-injektion er en sikkerhedssårbarhed, der opstår, når angribere indsætter ondsindet SQL-kode i et inputfelt, som applikationen ikke korrekt validerer eller saniterer.

Dette giver mulighed for at manipulere databaseforespørgsler, så angriberen kan omgå sikkerhedsforanstaltninger som autentifikation og autorisation, eller tilgå og ændre data direkte.

---

## Typer af SQL Injektion
### Klassisk SQL Injektion
Opstår, når en applikation direkte inkluderer brugerinput i en SQL-forespørgsel uden korrekt validering eller sanitering. 
Angriberen kan indsætte skadelig SQL-kode i et inputfelt, der kan manipuleres til at køre vilkårlige SQL-kommandoer.

Dette udnytter typisk dynamisk opbyggede SQL-forespørgsler, hvor input bliver sat ind direkte i SQL-strengen. 

---

#### Eksempel
I en sårbar applikation, der bruger dynamiske forespørgsler til at validere brugernavne, kan angriberen udnytte dette ved at indsætte ondsindet SQL-kode. 
Hvis webstedet returnerer forskelligt indhold afhængigt af en betingelse, kan angriberen udlede data.

```csharp
string query = "SELECT * FROM Users WHERE Username = '" + username + "'";
```

---

### Blind SQL Injektion
Her modtager angriberen ikke direkte fejlbeskeder fra serveren, men udnytter i stedet applikationens responsmønstre for at udlede information fra databasen. 
Blind SQL-injektion kræver, at angriberen systematisk tester forskellige input og observerer forskelle i svarene, f.eks. om en side loader korrekt eller ikke. 

---

#### Eksempel
I en sårbar applikation, der bruger dynamiske forespørgsler til at validere brugernavne, kan angriberen udnytte dette ved at indsætte ondsindet SQL-kode. 
Hvis webstedet returnerer forskelligt indhold afhængigt af en betingelse, kan angriberen udlede data.
Vi indsætter dette i username feltet:
```
' OR 1=1 --
```
Querien går så fra at være: 
```SQL
SELECT * FROM users WHERE username = '$username' AND password = '$password';
```
Til:
```SQL
SELECT * FROM users WHERE username = '' OR '1'='1' -- ' AND password = '$password';
```
I eksemplet **' OR 1=1 --**, fungerer **1=1** som en altid sand betingelse, hvilket gør, at hele SQL-forespørgslen bliver sand. 
Alt efter ``--``  ignoreres, og angriberen kan omgå valideringen.
Hvis dette input gives, vil det altid returnere en gyldig bruger, fordi **1=1** altid er sandt.

---

### Tidsbaseret SQL Injektion
 Her manipulerer angriberen forespørgsler for at skabe forsinkede responser fra serveren. 
 Ved at tjekke, hvor lang tid serveren er om at svare, kan angriberen udlede, om en forespørgsel er sand eller falsk, og på den måde gradvist opnå adgang til følsomme data.

---

#### Eksempel
```SQL
' OR IF(1=1, SLEEP(5), 0) --
```
Hvis betingelsen **1=1** er sand, vil serveren forsinke svaret med 5 sekunder. Hvis forespørgslen er falsk, vil der ikke være nogen forsinkelse.

```SQL
' OR IF((SELECT COUNT(*) FROM Users WHERE Username='admin') > 0, SLEEP(5), 0) --
```
Hvis en admin-bruger findes, vil svaret forsinkes, og angriberen kan konkludere, at brugeren eksisterer.

---

### Fejlbaseret SQL Injektion
Hvis en applikation returnerer detaljerede SQL-fejl, kan angribere bruge disse oplysninger til at forstå, hvordan databasen er opbygget, og dermed lettere udføre mere målrettede angreb.

For at beskytte mod dette bør applikationer undgå at give detaljerede fejlmeddelelser i produktion og i stedet logge dem internt.

---

#### Eksempel
Angriberen kan indsætte en forespørgsel, der bevidst forårsager en SQL-fejl, og bruge fejlmeddelelsen til at få information om databasen.
```
' OR 1=1 UNION SELECT null, version() --
```

Dette kan resultere i, at applikationen returnerer en fejlmeddelelse, der afslører databaseversionen eller strukturen. 
Hvis fejlmeddelelser returneres til brugeren, kan angriberen bruge disse oplysninger til at udføre yderligere angreb.

---

## Example
A simple example of an SQL injection attack is manipulating a login form.

Suppose we have the following SQL query:
```sql
SELECT * FROM users WHERE username = 'username' AND password = 'password';
```

If an attacker inputs the following:

- `username`: `admin' --`
- `password`: `anything`

The resulting query becomes:
```sql
SELECT * FROM users WHERE username = 'admin' -- ' AND password = 'anything';
```

The `--` comment marker causes the rest of the query to be ignored, potentially allowing the attacker to bypass authentication.

---

## Consequences
- Unauthorized access to data
- Data corruption or deletion
- Loss of data integrity
- Exposure of sensitive information
- Potential control over the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] server

---

## Prevention Techniques
##### Parameteriserede Queries
Dette indebærer, at SQL-forespørgslen ikke direkte integrerer brugerinput, men i stedet bruger parametre, der sendes separat til databasen. 
Dette adskiller selve SQL-koden fra dataene og forhindrer, at ondsindet input kan udføres som SQL-kommandoer.

Her ved systemet at @username parameteren er en streng/nvarchar og behandler derfor hele parameteren som 1 streng og kan opfattes som andre datatyper ved at lave f.eks. -- og ' osv.

###### Eksempel (usikker dynamisk SQL)
```csharp
string query = "SELECT * FROM Users WHERE Username = '" + username + "' AND Password = '" + password + "'";
```

###### Eksempel (sikker med parameteriseret forespørgsel)
```csharp
string query = "SELECT * FROM Users WHERE Username = @username AND Password = @password";
using (SqlCommand cmd = new SqlCommand(query, connection)) {
    cmd.Parameters.AddWithValue("@username", username);
    cmd.Parameters.AddWithValue("@password", password);
    ...
```

---

##### Stored Procedures
Brug [[Stored Procedures]]s til [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] queries fordi de er præ-kompileret og mixer ikke user input med kode.
```sql
CREATE PROCEDURE GetUser
@username NVARCHAR(50),
@password NVARCHAR(50)
AS
BEGIN
    SELECT * FROM users WHERE username = @username AND password = @password;
END
```

---

##### Input Validation
Validér og sanitér alle brugerinput for at sikrer at de er på det forventede format.

---

##### ORM Frameworks
Object-Relational Mapping frameworks, som Entity Framework håndterer automatisk parameterisering og kan reducere risici for SQL injektion

---

##### Least Privilege Principle
Ensure that the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] account used by the application has the minimum privileges necessary to perform its operations.
Sikr at [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] accountet der bliver brugt af applikationen, kun har de privilegier der er nødvendige, for at lave de operationer de skal.

---

##### Security Tools
Utilize web application firewalls (WAFs) and other security tools to detect and block SQL injection attempts.
Brug web application firewalls (WAFs) og andre sikkerhedsværktøjer til at finde og blokere SQL-injektion forsøg.

---

## Related Topics
- [[Uge44.5 - SQL Injektion|SQL Injektion Opgaver]]
- 

---

## Resources
- [SQL Injektion Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_23/scormcontent/index.html#/lessons/sG8B6Sv5lFGLNCi_DpgX9FGw2i3hww52)
- [SQL Injektion Video](https://www.youtube.com/watch?v=ciNHn38EyRc)