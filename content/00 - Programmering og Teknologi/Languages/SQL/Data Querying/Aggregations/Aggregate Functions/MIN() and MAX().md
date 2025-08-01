tags: #Programmering #SQL

## Definition 
---
`MIN()`-funktionen returnerer den mindste værdi af den valgte kolonne
`MAX()`-funktionen returnerer den højeste værdi af den valgte kolonne
## MIN() eksempel
---
Find den mindste pris i `Price`-kolonnen:
```SQL
SELECT MIN(Price)  
FROM Products;
```
## MAX() eksempel
---
Find den højeste pris i `Price`-kolonnen:
```SQL
SELECT MAX(Price)  
FROM Products;
```


## Sæt kolonnenavn (Alias)
---
Når man bruger `MIN()` og `MAX()`, vil den returnerede kolonne intet navn have.
For at give den et navn, kan man bruge `AS`-keywordet:
```SQL
SELECT MIN(Price) AS SmallestPrice  
FROM Products;
```


## Related Topics
---
- [[SELECT]]
- 

## Resources
---
- [MIN() and MAX()](https://www.w3schools.com/sql/sql_min_max.asp)
- 