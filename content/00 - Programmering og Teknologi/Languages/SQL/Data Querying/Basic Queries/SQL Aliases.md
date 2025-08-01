tags: #Programmering #SQL

## Definition 
---
SQL aliases bliver brugt til at give en [[Table|tabel]] eller en kolonne i en tabel, et midlertidigt navn.
Aliasser bliver ofte brugt til at lave kolonnenavne mere læselige.

Et alias eksisterer kun i den query, det bliver defineret.
Et alias bliver laves med `AS`-keyworded.
## Syntax
---
Brugt på på kolonne:
```SQL
SELECT _column_name_ AS _alias_name_  
FROM _table_name;_
```

Brugt på tabel:
```SQL
SELECT _column_name(s)_  
FROM _table_name_ AS _alias_name;_
```
### Example
---
```SQL
SELECT CustomerID AS ID  
FROM Customers;
```

I de fleste databasesprog kan `AS` undlades helt, med samme resultat.
```SQL
SELECT CustomerID ID  
FROM Customers;
```

## Hvornår bruges de?
---
Aliasser kan være brugbare når:

- Der er mere end 1 tabel involveret i en query
- Funktioner bliver brugt queryen
- Kolonnenavne er lange og ikke særligt læselige
- 2 eller flere kolonner er kombineret 


## Related Topics
---
- [[SELECT]]
- 

## Resources
---
- [SQL Aliases](https://www.w3schools.com/sql/sql_alias.asp)
- 