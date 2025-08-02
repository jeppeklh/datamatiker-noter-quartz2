tags: #Programmering #SQL #SQLBasics #Statement

> [!tldr] Definition
> The `INSERT` statement is used to add new rows of data to a [[Table]]. 

It allows you to specify the columns for which you want to insert values and the values to be inserted.

---

## Syntax
```SQL
INSERT INTO tabel_navn (kolonne1, kolonne2, kolonne3, ...)
VALUES (værdi1, værdi2, værdi3, ...);
```

Hvis du giver værdier til kun en del af kolonnerne i en INSERT INTO-sætning, skal du eksplicit angive de kolonner, du ønsker at indsætte værdier i. 
De øvrige kolonner, som du ikke giver værdier til, skal enten have en standardværdi defineret eller tillade NULL værdier.

---

### Example
```SQL
INSERT INTO Participant (Email, FirstName, LastName, ImagePath, SemesterId)
VALUES ('john.doe@example.com', 'John', 'Doe', '/images/johndoe.png', 2);
```

---

## Eksempel: Standardværdier

Vi bruger eksemplet fra [[Database Design]].
![[Databasemodel eksempel 4.png]]

Antag, at du kun vil indsætte data i kolonnerne Email, FirstName, og LastName i Participant-tabellen, angive en standardværdi for kolonnen SemesterId og lade ImagePath stå tomme (forudsat at den tillader NULL værdi).

**Tilføj standardværdi til SemesterId**
```SQL
ALTER TABLE Participant
ADD CONSTRAINT DF_SemesterId DEFAULT 1 FOR SemesterId;
```

**Indsættelse i udvalgte kolonner**
```SQL
INSERT INTO Participant (Email, FirstName, LastName)
VALUES ('john.doe@example.com', 'John', 'Doe');
```
I dette eksempel vil værdi for og SemesterId være lige med 1 og ImagePath være NULL, hvis den tillader NULL værdi. 

Hvis den ikke tillader NULL værdi, vil indsættelsen fejle.

---

## IDENTITY-begrænsning
Når en kolonne i en tabel har en IDENTITY-begrænsning, betyder det, at denne kolonne automatisk genererer en unik værdi for hver ny række, der indsættes i [[Table|tabellen]]. 
Typisk bruges en IDENTITY-kolonne til at generere [[PRIMARY KEY|primærnøgler]].

Lad os antage, at SemesterId-kolonnen i Semester-tabellen er blevet defineret med en IDENTITY-begrænsning:

```SQL
CREATE TABLE Semester (
  SemesterId Int IDENTITY(1,1) PRIMARY KEY,
  Number Int NOT NULL
);
```

Når du indsætter en ny række i en tabel, der har en IDENTITY-kolonne, behøver du ikke (og kan ikke) specificere en værdi for denne kolonne. 
```SQL
INSERT INTO Semester (Number)
VALUES (3);
```

---

## Indsættelse af værdier for alle kolonner uden at specificere dem
På denne måde udelader du kolonnenavnene og angiver blot værdierne i samme rækkefølge som kolonnerne er defineret i tabellen. Denne metode er enkel, når du vil indsætte data i alle kolonner.

---

### Syntax
```SQL
INSERT INTO tabel_navn
VALUES (værdi1, værdi2, værdi3, ...);
```

---

### Eksempel
```SQL
INSERT INTO Participant
VALUES ('jane.doe@example.com', 'Jane', 'Doe', '/images/janedoe.png', 3);
```

---

## Indsættelse af flere rækker
For at tilføje flere rækker i en enkelt INSERT INTO-sætning kan du angive flere værdigrupper, adskilt af kommaer.
### Syntax
---
```SQL
INSERT INTO table_name (column1, column2, column3, ...)
VALUES 
    (value1, value2, value3, ...),
    (value1, value2, value3, ...),
    (value1, value2, value3, ...);
```

---

### Eksempel
```SQL
INSERT INTO PARTICIPANT (Email, FirstName, LastName, ImagePath, SemesterId)
VALUES 
    ('jens@example.com', 'Jens', 'Hansen', 'path/to/image1.jpg', 1),
    ('pia@example.com', 'Pia', 'Larsen', 'path/to/image2.jpg', 1),
    ('patrick@example.com', 'Patrick', 'Andersen', 'path/to/image3.jpg', 1);
```

---

## Related Topics
- [[SQL Syntax|SQL Syntax]]
- [[SELECT]]
- [[UPDATE]]
- [[DELETE]]
- [[CREATE TABLE]]
- [[ALTER TABLE]]
- [[DROP TABLE]]

---

## Resources
- [DML Læringsobjekt (INSERT INTO)](https://scorm.itslearning.com/data/3289/C20150/ims_import_14/scormcontent/index.html#/lessons/GZ4kNe6JGOR8GYkRrkf0C3SUldV5N4c9)
- 