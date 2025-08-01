SQL INJEKTION Dette opgavesæt giver dig praktisk erfaring med at sikre en database mod SQL-injektion og forståelse af datasikkerhed gennem kryptering. Du vil få mulighed for at udføre SQL-injektioner og lære metoder til at beskytte mod dem i en .NET-kontekst.

Du har som en del af forberedelsen til i dag læst omkring SQL injektioner. Hvis du som programmør ikke har taget højde for denne problematik i dine løsninger, så er du sårbar overfor, at en ondsindet aktør kan udføre tilfældige kommandoer imod din database. Du vil i disse deløvelser blive holdt i hånden til at udføre et aktuelt SQL-angreb. Det skal siges, at det ikke er tilladt at benytte denne viden til at angribe andre hjemmesider på internettet end den side, som I vil blive præsenteret for i denne øvelse (du vil blive retsforfulgt jvf. Straffeloven §263). Du vil du se på, hvordan du som programmør i en .NET verden, kan undgå denne problematik.

## Øvelse 1: Terminologi
---
Forventning: At opnå en grundlæggende forståelse af SQL-injektion, dets funktion og de risici, det medfører for applikationer og databaser.

Brug "Ordet rundt" til at reflektere over begreberne:

**Forklar SQL-injektion: Hvad er SQL-injektion, og hvordan kan det bruges til at manipulere en database?**
	SQL-injektion er en sårbarhed, hvor en angriber manipulerer SQL-forespørgsler ved at indsætte ondsindet kode i inputfelter, hvilket kan give adgang til data, ændre data eller endda skade en database.

**Risikoanalyse: Diskuter, hvilke typer data der er mest udsatte for SQL-injektion i en webshop. Hvilke konsekvenser kan det have for både webshoppen og kunderne, hvis sådanne data kompromitteres?**
	Særligt følsomme data inkluderer kundeoplysninger som navne, adresser og betalingsoplysninger. En SQL-injektion kan eksponere disse data og skade både virksomheden og kundernes privatliv.

**Eksempel på SQL-injektion: Gennemgå følgende sårbare forespørgsel og beskriv, hvordan en angriber kunne manipulere den:** 
```SQL
SELECT * FROM users WHERE username = '$username' AND password = '$password';
```
Skriv et eksempel på, hvad en angriber kunne indtaste som $username for at omgå adgangskontrollen.
```SQL
$username = ' OR '1'='1' --
```
Queries bliver til dette: 
```SQL
SELECT * FROM users WHERE username = '' OR '1'='1' -- ' AND password = '$password';
```

**Diskutér, hvordan SQL-injektionsangrebet påvirkede Sony PlayStation Network Hack (2011) eller Heartland Payment Systems Breach (2008) virksomheder og brugere.**
	SQL-injektion bidrog til bruddet på kundedata hos Sony. Det viste vigtigheden af sikring mod SQL-injektion, da det førte til mistet tillid og alvorlig omdømmeskade for Sony.

**Hvilke forebyggelsesstrategier kunne have beskyttet virksomheden mod SQL-injektion, og hvilke konsekvenser har sikkerhedsbrud som disse for virksomhedens omdømme og kundetillid?**
	[[SQL Injection#Use Prepared Statements (Parameterized Queries)|Parametriserede forespørgsler]] og [[SQL Injection#Input Validation|inputvalidering]] er essentielle. 
	Sådanne brud kan alvorligt skade en virksomheds omdømme og føre til mistet kundetillid.


## Øvelse 2: Typer af SQL-Injektion
---
Forventning: Forstå forskellige typer af SQL-injektion og hvordan hver type kan udnyttes.

#### Øvelse 2.1: Forskellige SQL-injektionstyper
---
**Opret en tabel der sammenligner de fire typer SQL-injektion**

· Klassisk SQL-injektion

· Blind SQL-injektion

· Tidsbaseret SQL-injektion

· Fejlbaseret SQL-injektion

| SQL-injektionstype        | Beskrivelse                                                                       |
| ------------------------- | --------------------------------------------------------------------------------- |
| Klassisk SQL-injektion    | Manipulerer forespørgsler direkte gennem ondsindede input                         |
| Blind SQL-injektion       | Anvender sandt/falsk spørgsmål for at opdage databasedetaljer uden direkte output |
| Tidsbaseret SQL-injektion | Udnytter forsinkelser i databasen som respons for at finde sårbarheder            |
| Fejlbaseret SQL-injektion | Får databasen til at give fejlbeskeder med detaljer om dens struktur              |

#### Øvelse 2.2: Eksempler på Angreb
---
Givet forespørgslen:

```SQL
SELECT * FROM PRODUKT WHERE ProduktID = '$product_id';
```

**Hvordan kunne en blind SQL-injektion bruges til at finde ud af, om en bestemt produkt-id findes i webshop-databasen?**
	Kan afsløre data ved gradvist at teste for tilstedeværelsen af en specifik produkt-ID.
	
Sættes ind på ProdukctID's plads:
```SQL
' AND (SELECT COUNT(*) FROM Produkt WHERE ProductId = 1) > 0 --
```
Querien bliver til:
```SQL
SELECT * FROM PRODUKT 
WHERE ProduktID = '' 
OR (SELECT COUNT(*) FROM PRODUKT WHERE ProduktID = 1) > 0 --;
```


**Hvordan kan tidsbaseret SQL-injektion bruges til at afgøre, om en sårbarhed er til stede?**
	Kan teste sårbarheder ved at indsætte kommandoer, som forsinker serverens respons.

Sættes ind på ProdukctID's plads:
```SQL
' OR IF((SELECT COUNT(*) FROM PRODUKT WHERE ProduktID=1) > 0, SLEEP(5), 0) --
```
Querien bliver til:
```SQL
SELECT * FROM PRODUKT 
WHERE ProduktID = '' 
OR IF((SELECT COUNT(*) FROM PRODUKT WHERE ProduktID=1) > 0, SLEEP(5), 0) --';
```
#### Øvelse 2.3: Praktisk SQL-injektion
---
Du og din gruppe skal i denne øvelse se nærmere på, hvordan et konkret SQL injektionsangreb ser ud. Tag jer god tid til at forstå, hvad der sker – trin for trin.

Fremgangsmåde: · Gå ind på https://www.hacksplaining.com/exercises/sql-injection

#### Øvelse 2.4: Hvordan undgår vi SQL-injektion
---
Efter ovenstående øvelse er udført, bliver du ført videre til en side med gode råd om, hvordan man kan undgå SQL injektioner i forskellige programmeringssprog. Forhold dig kursorisk (læs: skim) til rådene på siden, men se om du kan finde noget på listen, som du har kendskab til. Vend det, som du har fundet frem til med dit team. 

## Øvelse 3: Detektion af SQL-Injektion
---

Forventning: Lære at identificere SQL-injektionssårbarheder i en webshop-database og at få praktisk erfaring med at opdage SQL-injektionsforsøg i en database gennem realtidsprofilering.

Scenarie:

Din webshop-database har mistanke om SQL-injektioner mod kundeoplysninger og ordredata. Som databaseadministrator skal du opsætte overvågning og logning, analysere forespørgsler, og identificere mulige angreb.

#### Øvelse 3.1: Identifikation gennem Kodegennemgang
---
**Gennemgå følgende kode og identificer, om der er en SQL-injektionssårbarhed. Hvis ja, forklar, hvordan den kan misbruges.**

```csharp
query = "SELECT * FROM SHOPPINGCART WHERE CustomerID = ‘” + user_input + "';"
```
Er sårbar, da user_input tilføjes uden validering, hvilket kan føre til injektionsangreb.
#### Øvelse 3.2: Opsætning af SQL Server Profiler for Realtidsdetektion
---
Udfør følgende på SQL Server Management Studio:

- Åbn SQL Server Management Studio (SSMS) og start SQL Server Profiler.

- Opret en ny sporing i SQL Server Profiler:

	- Vælg skabelon: Vælg en standard skabelon, der fanger SQL-statements (Standard eller TSQL_SPs).
	
	- Filtrering: Under "Events Selection", vælg kun de nødvendige begivenheder for at reducere støj.
	
	- Aktiver filtrering for at logge forespørgsler, der indeholder kommandoer som ``UNION``, ``OR``, ``--,`` og ``;``, da disse ofte bruges i SQL-injektioner.

- Overvågning af Profileringsdata:

	- Lad profileringssessionen køre og udfør en række testforespørgsler mod webshop-databasen.
	
	- Testforespørgsel 1 (klassisk SQL-injektion): 
```SQL
SELECT * FROM SHOPPINGCART WHERE OrderID = 1 OR 1=1;
```

Testforespørgsel 2 (fejlbaseret injektion): 

```SQL
SELECT * FROM CUSTOMER WHERE CustomerID = '1' OR '1'='1' --';
```
 Testforespørgsel 3 (blind SQL-injektion): 
```SQL
SELECT * FROM PRODUCT WHERE ProductID = 1 AND (SELECT COUNT(*) FROM CUSTOMER) = 1;
```

**Overvåg SQL Server Profiler for at se, hvordan disse forespørgsler fanges og analyser strukturen for hver forespørgsel.**

- Dokumentér Mistænkelige Forespørgsler:

	- Notér mindst én forespørgsel fra sporingens output, der ligner et injektionsforsøg.
	
	- Forklar, hvorfor du mener, at denne forespørgsel er mistænkelig, og hvad den forsøger at opnå.

## Øvelse 4: Forebyggelse af SQL-Injektion
---
Forventning: At forstå og anvende teknikker til at beskytte en webshop-database mod SQL-injektion.

#### Øvelse 4.1: Anvendelse af Parameteriserede Forespørgsler
---
Rediger den sårbare forespørgsel fra Øvelse 3.1, så den anvender parameteriserede forespørgsler. Forklar, hvorfor dette hjælper med at forhindre SQL-injektion.

#### Øvelse 4.2: Refaktorisering af Repository Pattern
---
**Gennemgå følgende kode i en repository klasse, som indeholder en metode til at hente ordreoplysninger baseret på en kunde-ID:** 

```csharp
public List <ShoppingCart> GetOrdersByCustomerId(string customerId)
{
	var query = "SELECT * FROM SHOPPINGCART WHERE CustomerId = '{customerId}'";	
	using (var connection = new SqlConnection(connectionString))
	{
		var command = new SqlCommand(query, connection);
		connection.Open();
		var reader = command.ExecuteReader();
		var orders = new List<ShoppingCart>();
		
		while (reader.Read())
		{
			orders.Add(new ShoppingCart
			{
				OrderId = (int)reader["OrderId"],
				OrderDate = (DateTime)reader["OrderDate"],
				// udfyld øvrige felter her
			});
		}
		return orders;
	}
}
```

- Identificér, hvorfor koden er sårbar over for SQL-injektion.

- Refaktorer GetOrdersByCustomerId-metoden til at bruge parameterisering i stedet for direkte indsættelse af customerId.
```csharp
public List<ShoppingCart> GetOrdersByCustomerId(string customerId) 

{ 
    var query = "SELECT * FROM SHOPPINGCART WHERE CustomerId = @CustomerID"; 
    using (var connection = new SqlConnection(connectionString)) 
    { 
        var command = new SqlCommand(query, connection); 
	    command.Parameters.AddWithValue("@CustomerID", CustomerID); 
        connection.Open(); 
        var reader = command.ExecuteReader(); 
        var orders = new List<ShoppingCart>(); 
        while (reader.Read()) 
        { 
            orders.Add(new ShoppingCart 
            { 
                OrderId = (int)reader["OrderId"], 
                OrderDate = (DateTime)reader["OrderDate"], 
                // udfyld øvrige felter her 
            }); 
        } 
        return orders; 
    } 
}
```

**Test Den Refaktorerede Kode:**

- Kør en test med både gyldige og mistænkelige customerId-værdier, fx "; DROP TABLE SHPPINGCART; -- eller 1=1, og verificér, at koden nu er beskyttet mod SQL-injektion.

- Valider, at dataudtrækket stadig fungerer som forventet.

Gennemgå hele repository-klassen og identificér andre metoder, der potentielt bruger dynamisk SQL.

Refaktorér alle fundne metoder til at bruge parameteriserede forespørgsler.

#### Øvelse 4.3: Værktøjer til SQL-Injektionsdetektion
---
**Undersøg værktøjer som SQLMap og OWASP ZAP og diskuter i gruppen, hvordan disse kan hjælpe udviklere med at detektere og afhjælpe SQL-injektionssårbarheder.**

**SQLMap** og **OWASP ZAP** kan automatisere detektering og afhjælpning af SQL-injektionssårbarheder.

## Øvelse 5: Kryptering og Sikker Datahåndtering
---
Forventning: At forstå, hvordan kryptering kan beskytte følsomme data i webshop-databasen, selv hvis SQL-injektion skulle lykkes.

#### Øvelse 5.1: Kryptering af Følsomme Data
---
**Forklar forskellen mellem kryptering af data “i hvile” og “under transmission.” Hvorfor er begge typer relevante i en webshop, der håndterer personlige data?**

Kryptering i hvile beskytter data lagret på serveren. 
Kryptering under transmission beskytter data under overførsel. 
Begge typer er vigtige for at beskytte mod SQL-injektion.
#### Øvelse 5.2: Praktisk Kryptering
---
Opret en kolonne til lagring af krypterede kreditkortoplysninger og anvend en simpel krypteringsnøgle.

Lav 2 Kolonner (CreditCard skal indeholde den krypterede data):
```SQL
ALTER TABLE CUSTOMER
ADD CreditCard VARBINARY(MAX), CreditCard2 NVARCHAR(MAX);
```

Lav krypteringnøglen:
```SQL
CREATE SYMMETRIC KEY MyAESKey WITH ALGORITHM = AES_256 
ENCRYPTION BY PASSWORD = ‘1234’;
```

Kryptering:
```SQL
OPEN SYMMETRIC KEY MyAESKey 
DECRYPTION BY PASSWORD = '1234';  
UPDATE CUSTOMER 
SET CreditCard = ENCRYPTBYKEY(KEY_GUID('MyAESKey'), CAST(CreditCard2 AS NVARCHAR(MAX)));  
CLOSE SYMMETRIC KEY MyAESKey;
```

Dekryptering: 
```SQL
OPEN SYMMETRIC KEY MyAESKey 
DECRYPTION BY PASSWORD = '1234'; 
SELECT CONVERT(NVARCHAR(MAX), DECRYPTBYKEY(CreditCard)) AS DecryptedData 
FROM CUSTOMER WHERE CustomerID = 1; 
CLOSE SYMMETRIC KEY MyAESKey;
```

Dokumentér processen og beskriv, hvordan denne praksis reducerer risici i tilfælde af et SQL-injektionsangreb.

Tidsramme: 30 minutter

## Øvelse 6: Vidensdeling kl. 14:30
---
Forventning: At evaluere, hvad du har lært om SQL-injektion, herunder de forskellige typer angreb, metoder til detektion og forebyggelse af SQL-injektion samt sikring af databaser mod disse sårbarheder.

· Diskutér, hvordan de forskellige typer SQL-injektion kan bruges til at udnytte sårbare SQL-forespørgsler.

· Forklar kort parameteriserede forespørgsler og beskriv, hvordan de blev anvendt i din løsning.

· Beskriv, hvordan du ville beskytte en webshop-database mod SQL-injektion ved brug af detektions- og forebyggelsesmetoder.

Tidsramme: 30 minutter