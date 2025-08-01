tags: #Programmering #SQL

## Definition 
---
`LIKE` bliver brugt i en `Where`-clause for at søge efter et specificeret mønster i en kolonne.

Der er 2 [[Wildcards]] der ofte bliver brugt sammen med `LIKE`:
- `%` Repræsenterer nul, et, eller flere characters.
- `_` Repræsenterer ét enkelt character.
## Syntax
---
```SQL
SELECT _column1, column2, ..._  
FROM _table_name_  
WHERE _columnN_ LIKE _pattern_;
```
### Example
---
Vælg alle `Customers` der starter med a.
```SQL
SELECT * FROM Customers  
WHERE CustomerName LIKE 'a%';
```


## Header2
---



## Related Topics
---
- [[Wildcards]]
- [[SELECT]]
- [[WHERE]]

## Resources
---
- Link
- 