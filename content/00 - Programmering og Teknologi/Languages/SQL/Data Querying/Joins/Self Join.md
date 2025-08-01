tags: #Programmering #SQL

## Definition 
---
Self join er en [[Joins|join]], men [[Table|tabellen]] bliver joinet med sig selv.
## Syntax
---
```SQL
SELECT column_name(s)  
FROM table1 T1, table1 T2  
WHERE condition;
```
_T1_ and _T2_ are different table aliases for the same table.

### Example
---
Match `customers` der er fra den samme by:
```SQL
SELECT A.CustomerName AS CustomerName1, B.CustomerName AS CustomerName2, A.City  
FROM Customers A, Customers B  
WHERE A.CustomerID <> B.CustomerID  
AND A.City = B.City  
ORDER BY A.City;
```


## Header2
---



## Related Topics
---
- [[SELECT]]
- [[WHERE Clause|WHERE]]
- [[AND Operator|AND]]
- [[ORDER BY Clause|ORDER BY]]
- [[Joins]]

## Resources
---
- [JOINS Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_17/scormcontent/index.html#/lessons/Xh1h5Fdn8KpTJAPPs09i5HcJfDfpkvGT)
- [SQL Self Join](https://www.w3schools.com/sql/sql_join_self.asp)