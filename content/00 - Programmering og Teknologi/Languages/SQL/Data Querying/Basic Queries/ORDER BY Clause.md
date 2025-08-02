tags: #Programmering #SQL

> [!tldr] Definition
> `ORDER BY` bruges til at sortere [[Data|data]] i enten ascending eller descending rækkefølge.

---

## Syntax
```SQL
SELECT _column1_, _column2, ..._  
FROM _table_name_  
ORDER BY _column1, column2, ..._ ASC|DESC;
```

---

### Example
Sorterer producter baseret på pris.
```SQL
SELECT * FROM Products  
ORDER BY Price;
```

---

## DESC
`ORDER BY` sorterer [[Data|data]] i ascending rækkefølge som udgangspunkt.
For at sortere i descending rækkefølge bruger vi `DESC`-keywordet:

```SQL
SELECT * FROM Products  
ORDER BY Price DESC;
```

Dette sorterer produkterne fra højest til lavest pris.

---

## ORDER BY - flere kollonner
Det følgende SQL statement vælger alle kunder fra Customers-[[Table|tabellen]], sorteret på `Country`- og `CustomerName`-kolonnen. 
Dette betyder at det sorterer baseret `Country` men hvis nogle rækker har den samme `Country`-værdi, sorterer den dam på `CustomerName`

```SQL
SELECT * FROM Customers  
ORDER BY Country, CustomerName;
```

---

## Related Topics
- [[SELECT]]
- 

---

## Resources
- [Sql Order By](https://www.w3schools.com/sql/sql_orderby.asp)
- 