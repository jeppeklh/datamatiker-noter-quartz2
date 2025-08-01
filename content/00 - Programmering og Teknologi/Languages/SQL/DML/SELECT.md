tags: #Programmering #SQL #SQLBasics #Statement

## Definition 
---
The `SELECT` statement is used to retrieve data from one or more [[Table|tables]] in a [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]]. 

`SELECT` bliver brugt til at vælge data fra en eller flere [[Table|tabeller]] i en [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]].

Det er den mest brugte SQL command og kan bruges til at specificere kolonnerne der skal vælges, og hvilken tabel det skal vælges fra.

## Syntax
---
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
### Example
---
```sql
SELECT first_name, last_name
FROM employees
WHERE department = 'Sales';
```

## SELECT ALL 
---
Hvis man vil returnere alle kolonner i en [[Table|tabel]], uden at specificere hver kolonnenavn, can man bruge `SELECT *` syntaksen.

```SQL
SELECT * FROM Customers;
```
## Related Topics
---
- [[SQL Syntax|SQL Syntax]]
- [[WHERE Clause|WHERE]]
- 

## Resources
---
- [Select](https://www.w3schools.com/sql/sql_select.asp)
- 


