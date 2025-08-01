tags: #Programmering #SQL

## Definition 
---
`CASE`-expressionen går gennem conditions og returnerer en værdi når den første condition er opfyldt. (Lige som en [[If-variants#if-else|if-else]]).

Så når en condition er `TRUE`, stopper den med at læse og returnerer resulatet. 
Hvis ingen condition er sand, returnerer den værdien i `ELSE`-klausulen.
Hvis der ingen `ELSE`-klausul er, og ingen condition er `TRUE`, bliver der returneret `NULL`.
## Syntax
---
```SQL
CASE  
    WHEN condition1 THEN _result1 
    WHEN condition2 THEN result2  
    WHEN conditionN THEN resultN  
    ELSE result 
END;
```
### Example
---
Sortér  customers efter `City`. Hvis `City` er `NULL`, så sortér efter `Country`:
```SQL
SELECT CustomerName, City, Country  
FROM Customers  
ORDER BY  
(CASE  
    WHEN City IS NULL THEN Country  
    ELSE City  
END);
```


## Related Topics
---
- [[SELECT]]
- [[ORDER BY Clause|ORDER BY]]

## Resources
---
- [SQL Case](https://www.w3schools.com/sql/sql_case.asp)
- 