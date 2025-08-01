tags: #Programmering #SQL

## Definition 
---
`AVG()`-funktionen returnerer gennemsnittet af en numerisk kolonne.
`NULL`-værdier bliver ignoreret.

## Example
---
Find den gennemsnitlige pris for alle produkter:
```SQL
SELECT AVG(Price)  
FROM Products;
```

Her gives kolonnen et navn:
```SQL
SELECT AVG(Price) AS [average price]  
FROM Products;
```
Der bruges `[]` fordi der er et mellemrum.
## Højere end Gennemsnittet
---
Returnér alle produkter med en pris højere end gennemsnittet:
```SQL
SELECT * FROM Products  
WHERE price > (SELECT AVG(price) FROM Products);
```


## Related Topics
---
- Link
- 

## Resources
---
- [SQL Avg](https://www.w3schools.com/sql/sql_avg.asp)
- 