tags: #Programmering #SQL

> [!tldr] Definition
> `UNION`-operatoren bruges til at kombinere resultaterne fra 2 eller flere [[SELECT]]-statements.
>  - Hver [[SELECT]]-statement inde i en `UNION` SKAL have det samme antal kolonner.
>  - Kolonnerne skal have de samme [[SQL Data Types|datatyper]].
>  - Kolonnerne i hvert [[SELECT]]-statement skal også være i samme rækkefølge

`UNION` vælger kun distinkte værdier som udgangspunkt.

---

## Syntax
```SQL
SELECT column_name(s) FROM table1
UNION  
SELECT column_name(s) FROM table2;
```

---

### Example
Returnér de distinkte byer fra både `Customers`- og `Suppliers`-[[Table|tabellen]]:
```SQL
SELECT City FROM Customers  
UNION  
SELECT City FROM Suppliers  
ORDER BY City;
```

---

## UNION ALL
Tillader også duplikatværdier.

Retunér alle byer (også duplikatværdier) fra både `Customers`- og `Suppliers`-[[Table|tabellen]]:
```SQL
SELECT City FROM Customers  
UNION ALL  
SELECT City FROM Suppliers  
ORDER BY City;
```

---

## SQL UNION med WHERE
Retunér de distinkte tyske byer fra både `Customers`- og `Suppliers`-[[Table|tabellen]]`:
```SQL
SELECT City, Country FROM Customers  
WHERE Country='Germany'  
UNION  
SELECT City, Country FROM Suppliers  
WHERE Country='Germany'  
ORDER BY City;
```

---

## Related Topics
- [[ORDER BY Clause|ORDER BY]]
- [[WHERE Clause|WHERE]]
- [[SELECT]]

---

## Resources
- [SQL Union](https://www.w3schools.com/sql/sql_union.asp)
- 