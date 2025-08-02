tags: #Programmering #SQL

> [!tldr] Definition
> `SUM()`-funktionen returnerer summen af en numerisk kolonne.

---

## Syntax 
```SQL
SELECT SUM(column_name)  
FROM table_name  
WHERE condition;
```

---

### Example
Returnér summen af alle `Quantity` fields i `OrderDetails`-[[Table|tabellen]]:
```SQL
SELECT SUM(Quantity)  
FROM OrderDetails;
```

---

## SUM() med en Expression
Hvis hvert produkt i `OrderDetails`-tabellen koster 10 dollars, kan vi finde den totale intjening i dollars ved at gange kvatiteten med 10:
```SQL
SELECT SUM(Quantity * 10)  
FROM OrderDetails;
```

---

## Related Topics
- [[WHERE Clause|WHERE]]
- [[SELECT]]

---

## Resources
- [SQL Sum](https://www.w3schools.com/sql/sql_sum.asp)
- 