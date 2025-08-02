---
aliases:
  - Data Definition Language
---
tags: #Programmering #SQL #DDL

> [!tldr] Definition
> Data Definition Language (DDL) bruges til at definere og administrere strukturen af en database. 

DDL inkluderer kommandoer, der tillader brugere at oprette, ændre og slette databaseobjekter som [[Table|tabeller]], indekser og skemaer.

DDL statements do not manipulate data but rather define the schema of the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]]. They are critical for setting up the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] structure and maintaining it over time.

---

## Subtopics
- [[CREATE TABLE|Creating Tables]]
- [[ALTER TABLE|Altering Tables]]
- [[DROP TABLE|Dropping Tables]]
- [[CREATE INDEX|Creating Indexes]]

---

## Key DDL Commands 
- **CREATE**: Bruges til at oprette nye databaseobjekter som tabeller, indekser og visninger.

- **ALTER**: Bruges til at ændre strukturen af eksisterende databaseobjekter, f.eks. tilføjelse af nye kolonner eller ændring af constraint-specifikationer.

- **DROP**:  Bruges til at slette eksisterende databaseobjekter, hvilket permanent fjerner dem og deres data fra databasen.

- **TRUNCATE**: Bruges til at fjerne alle rækker fra en tabel, men bevarer selve tabelstrukturen.

---

## Anvendelse
Når en database er designet, for eksempel via en UML-databasemodel, bruges DDL til at implementere denne model i en SQL-database. 
Processen starter med oprettelse af databasen, efterfulgt af oprettelse af tabeller med korrekte nøgler og constraints.

Med DDL kan du også administrere eksisterende databaser, som f.eks. at tilføje nye kolonner til en tabel eller ændre datatyper, og til sidst slette uønskede objekter, når de ikke længere er nødvendige.

---

## Related Topics
- Link
- 

---

## Resources
- [DDL Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_9/scormcontent/index.html#/lessons/1QbXTBeuRKvptwBpGDgjXVOZoZNzPE-V)
- [DDL Youtube video](https://www.youtube.com/watch?v=0xINwDcFLSk)