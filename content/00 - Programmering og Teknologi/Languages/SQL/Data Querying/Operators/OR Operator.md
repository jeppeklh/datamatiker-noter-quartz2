tags: #Programmering #SQL

> [!tldr] Definition
> `WHERE` kan indeholde 1 eller mange `AND` operators.
> `AND` bruges til at filtrere [[Data|data]] baseret på mere end 1 condition.

---

## Syntax
```SQL
SELECT _column1_, _column2, ..._  
FROM _table_name_  
WHERE _condition1_ OR _condition2_ OR _condition3 ..._;
```

---

### Example
Vælg alle `Customers` fra Tyskland eller Spanien
```SQL
SELECT *  
FROM Customers  
WHERE Country = 'Germany' OR Country = 'Spain';
```

---

## Related Topics
- [[SELECT]]
- [[WHERE Clause|WHERE]]
- [[AND Operator|AND]]

---

## Resources
- Link
- 