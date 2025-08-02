tags: #Programmering #SQL

> [!tldr] Definition
> Når du arbejder med [[PRIMARY KEY|primær]]- og [[FOREIGN KEY|fremmednøgler]] i forbindelse med [[DML Overview|DML]], er der flere vigtige overvejelser at tage hensyn til for at sikre dataintegrereten.

---

## Primærnøgle
En [[PRIMARY KEY|primærnøgle]] er en kolonne eller et sæt af kolonner i en tabel, der unikt identificerer hver række i tabellen. Når du indsætter eller opdaterer data, er der nogle nøgleprincipper:

---

##### Unikhed
Værdierne i en primærnøglekolonne skal være unikke. Dette betyder, at hver række i tabellen skal have en unik værdi for primærnøglen. Hvis du forsøger at indsætte en række, hvor primærnøgleværdien allerede eksisterer i tabellen, vil databasen kaste en fejl.

---

##### Ikke-null
En primærnøglekolonne kan ikke indeholde NULL værdier. Når du indsætter eller opdaterer data i en tabel, skal du sikre, at kolonnen eller kolonnerne, der udgør primærnøglen, altid har en gyldig værdi.

---

## Fremmednøgle
En [[FOREIGN KEY|fremmednøgle]] er en kolonne eller et sæt af kolonner i en tabel, der refererer til en [[PRIMARY KEY|primærnøgle]] i en anden [[Table|tabel]]. 
 Overvejelserne her inkluderer:

---

##### Referentiel Integritet
Når du indsætter eller opdaterer en række, der indeholder en fremmednøgle, skal værdien i fremmednøglekolonnen eksistere som en primærnøgle i den refererede tabel. Dette betyder, at du ikke kan indsætte en række med en fremmednøgle, der refererer til en ikke-eksisterende værdi i den relaterede tabel.
```
INSERT INTO PARTICIPANT (Email, FirstName, LastName, ImagePath, SemesterId) 
VALUES ('jens@example.com', 'Jens', 'Jensen', 'path/to/image.jpg', 2)
```
Hvis SemesterId = 2 ikke eksisterer i SEMESTER-tabellen, vil denne sætning mislykkes.

---

##### Cascading Actions
Afhængigt af hvordan fremmednøglerne er konfigureret, kan ændringer i den primære tabel (som sletning eller opdatering af en række) automatisk udløse tilsvarende ændringer i den tabel, der indeholder fremmednøglen. Dette kan være nyttigt til at opretholde dataens konsistens, men det kræver også forsigtighed for at undgå utilsigtede konsekvenser.

**Eksempel på en DELETE med ON DELETE CASCADE:** 
Hvis du sletter en række i SEMESTER-tabellen med SemesterId = 1, og der er en fremmednøgle med ON DELETE CASCADE, så vil alle rækker i PARTICIPANT, der refererer til SemesterId = 1, også blive slettet automatisk.

---

##### Sekvens af Operationer
 Når du indsætter data, skal du først sikre, at de relaterede data i den primære tabel allerede eksisterer. Det betyder typisk, at du først skal indsætte data i den tabel, der indeholder primærnøglen, før du indsætter data i den tabel, der indeholder fremmednøglen.

**Eksempel:** 
Du skal først indsætte en ny semester i SEMESTER-tabellen, før du kan tilføje en deltager i PARTICIPANT-tabellen, som refererer til det pågældende semester.

---

## Related Topics
- Link
- 

---

## Resources
- [DML Læringsobjekt (Sikring af Dataintegritet ved Dataændringer)](https://scorm.itslearning.com/data/3289/C20150/ims_import_14/scormcontent/index.html#/lessons/Xyek0mSehFMXpdlh9NoaDjoTpu7pIj9u)
- [DML Dataintegritet YouTube Video](https://www.youtube.com/watch?v=qhz7CpSepZ0)