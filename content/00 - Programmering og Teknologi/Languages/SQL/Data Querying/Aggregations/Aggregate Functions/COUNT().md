tags: #Programmering #SQL

> [!tldr] Definition
> `COUNT()`-funktionen returnerer antallet af rækker der matcher et givent kriterie.

---

## Syntax
```SQL
SELECT COUNT(column_name)  
FROM table_name  
WHERE condition;
```
### Example
---
Find mængden af rækker i `Products`-[[Table|tabellen]]:
```SQL
SELECT COUNT(*)  
FROM Products;
```

---

## Ignorér duplikater
Retúrner mængden af forskellige priser i `Products`-[[Table|tabellen]]:
```SQL
SELECT COUNT(DISTINCT Price)  
FROM Products;
```

---

## Related Topics
- [[WHERE Clause|WHERE]]
- [[SELECT]]

---

## Resources
- [SQL Count](https://www.w3schools.com/sql/sql_count.asp)
