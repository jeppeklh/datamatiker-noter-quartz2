---
aliases:
  - database
  - Databases
  - databases
---
tags: #Programmering #SQL #SQLBasics #Database

> [!tldr] Definition
> En organiseret samling af data, som er struktureret til at kunne tilgås, styres og opdateres elektronisk. 

> [!example] Eksempel
> Skolens database organiserer data om studerende, fag, underviserne og karakter osv.

---

## Components of a Database
- [[Table|Tables]]: The basic storage units within a database, holding the actual data.
- **Schemas**: Structures that define the organization of data within a database.
- **Indexes**: Structures that improve the speed of data retrieval operations.
- **Views**: Virtual tables based on the result-set of a query.
- **Stored Procedures**: Precompiled SQL queries that can be executed as needed.
- **Triggers**: Procedures that are automatically executed in response to certain events on a particular [[Table|table]] or view.

---

## Example
Here's a simple representation of a database named `CompanyDB`:

- **Employees Table**: Stores information about employees.
- **Departments Table**: Stores information about departments.

---

## Key Points
- **Relational Database**: A type of database that stores data in [[Table|tables]] with relationships between them ([[R-DBMS]]).
- **Non-relational Database**: A type of database that stores data in formats other than [[Table|tables]], such as document-based or key-value pairs.

---

## Faser
### Fase A: [[Database Design]]
Omfatter trinene til at designe en relationel databasemodel i UML med fokus på [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|domænemodellen]] som udgangspunkt og evt. med supplement af [[Datatypes|datatyper]] fra [[Design Class Diagram|DCD]]’et.

---

### Fase B: Database-implementering (SQL)
Omfatter trinene til at implementere en relationel database i et [[R-DBMS]] (MS SQL server) med udgangspunkt i den etablerede databasemodel i fase A med brug af SQL [[DDL Overview|Data Definition Language]] (SQL DDL).

---

### Fase C: Database-tilgang via Csharp og .NET
Omfatter trinene til at tilgå en relationel SQL-database (implementeret i fase B) fra et objekt-orienteret it-system via C# og .NET med brug af SQL [[Data Querying Overview|Data Query Language]] (SQL DQL) og SQL [[DML Overview|Data Manipulation Language]] (SQL DML)

---

## Related Topics
- [[SQL]]
- 

---

## Resources
- [Database læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_6/scormcontent/index.html#/lessons/R-uiHxV6wOoSodZUwqhx474w15v28DWY)
- [Databaseudvikling Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_6/scormcontent/index.html#/lessons/p250mgyFTtKx9adKq9-embXdLy25mngW)