tags: #Programmering #SQL #DataQuerying #Joins

> [!tldr] Definition
> **Joins** in SQL are used to combine rows from two or more [[Table|tables]] based on a related column between them. 

Joins are essential for querying relational [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|databases]] where data is spread across multiple [[Table|tables]].

---

## Subtopics
- [[Inner Join]]
- [[Left Join]]
- [[Right Join]]
- [[Full Join]]

---

### Example
```sql
SELECT a.column1, b.column2
FROM table1 a
JOIN table2 b ON a.common_column = b.common_column;
```

**`SELECT a.column1, b.column2`** 
  Jeg vil have ``column1`` fra ``a`` tabellen og ``column2`` fra ``b`` tabellen.

- **`FROM a`**
  Start med at kigge på ``a`` tabellen.
  
- **`JOIN b`**
  Join ``b`` tabellen med ``a`` tabellen, men inkluder kun rækker hvor conditionen nedenunder er sand.

- **`ON a.common_column = b.common_column`**
  ``common_column`` i ``a`` tabellen SKAL være lig med ``common_column`` i ``b`` tabellen.

---

## Related Topics
- Link
- 

---

## Resources
- [Joins Lærinsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_17/scormcontent/index.html#/lessons/KB7APLAcdHun_ihIXpYOFDKs8d--Mx14)
- [Joins further explaination](https://blog.jooq.org/say-no-to-venn-diagrams-when-explaining-joins/)