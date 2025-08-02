tags: #Programmering #SQL

> [!tldr] Definition
> `SELECT DISTINCT` bruges til at returnere kun distinkte values.
> I en [[Table|tabel]] kan en kollonne ofte have duplikat-værdier og nogen gange vil man kun have distinkte værdier. 

---

## Syntax
```SQL
SELECT DISTINCT column1, column2, ...  
FROM table_name;
```

---

### Example
Vælger alle forskellige lande fra Customer [[Table|tabellen]] :
```SQL
SELECT DISTINCT Country FROM Customers;
```

---

## Count Distinct
Ved at bruge `DISTINCT`-keywordet i en funktion kaldet `COUNT`, kan vi returnere antallet af distinkte lande:

```SQL
SELECT COUNT(DISTINCT Country) FROM Customers;
```

---

## Related Topics
- [[SELECT]]
- 

---

## Resources
- [Select Distinct](https://www.w3schools.com/sql/sql_distinct.asp)
- 