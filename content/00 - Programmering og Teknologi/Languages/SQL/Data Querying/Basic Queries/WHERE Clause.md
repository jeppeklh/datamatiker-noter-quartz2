tags: #Programmering #SQL

> [!tldr] Definition
> `WHERE` bruges til at filtrere [[Data|data]].
> Det bruges til kun at vælge det data der opfylder in bestemt condition.

---

## Syntax
```SQL
SELECT _column1_, _column2, ..._  
FROM _table_name_  
WHERE _condition_;
```

---

### Example
Vælger alle Customers fra Mexico.

```SQL
SELECT * FROM Customers  
WHERE Country='Mexico';
```

---

## Related Topics
- [[SELECT]]
- 

---

## Resources
- [SQL Where](https://www.w3schools.com/sql/sql_where.asp)
- 