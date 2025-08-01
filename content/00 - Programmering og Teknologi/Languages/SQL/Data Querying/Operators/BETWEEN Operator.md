tags: #Programmering #SQL

## Definition 
---
`BETWEEN`-operatoren vælger værdier indenfor en given rækkevide.
Værdierne kan være numre, tekst, eller datoer.
Start- og slutværdien er inkluderet.
## Syntax
---
```SQL
SELECT column_name(s)   FROM table_name   WHERE column_name BETWEEN value1 AND value2;
```
### Example
---
Vælg alle `Products` med en pris mellem 10 og 20:
```SQL
SELECT * FROM Products  
WHERE Price BETWEEN 10 AND 20;
```



## Related Topics
---
- [[AND Operator|AND]]
- [[WHERE Clause|WHERE]]
- [[SELECT]]
- 

## Resources
---
- [SQL Between](https://www.w3schools.com/sql/sql_between.asp)
- 