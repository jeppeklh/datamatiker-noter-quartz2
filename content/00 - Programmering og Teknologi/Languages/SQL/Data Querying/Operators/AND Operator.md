tags: #Programmering #SQL

## Definition 
---
`WHERE` kan indeholde 1 eller mange `AND` operators.
`AND` bruges til at filtrere [[Data|data]] baseret på mere end 1 condition.

## Syntax
---
```SQL
SELECT _column1_, _column2, ..._  
FROM _table_name_  
WHERE _condition1_ AND _condition2_ AND _condition3 ..._;
```
### Example
---
Vælg alle `Customers` fra Spanien, der starter med G.
```SQL
SELECT *  
FROM Customers  
WHERE Country = 'Spain' AND CustomerName LIKE 'G%';
```


## Kombinér AND og OR
---
Vælg alle `Customers` fra Spanien der starter med G eller R
Husk at bruge parenteser.
```SQL
SELECT * FROM Customers  
WHERE Country = 'Spain' AND (CustomerName LIKE 'G%' OR CustomerName LIKE 'R%');
```

Uden parenteser vil [[SELECT]] statementet returnere alle `Customers` fra Spanien der starter med G. Og derefter alle `Customers` uanset Land, der starter med R.
## Related Topics
---
- [[SELECT]]
- [[WHERE Clause|WHERE]]
- [[LIKE Operator|LIKE]]
- [[OR Operator|OR]]

## Resources
---
- [SQL And](https://www.w3schools.com/sql/sql_and.asp)
- 