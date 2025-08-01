tags: #Programmering #SQL

## Definition 
---
`IN`-operatoren bruges til at specificere flere værdier i en [[WHERE Clause|WHERE]]-klausul.
`IN` bruges altså som flere [[OR Operator|OR]] conditions-

## Syntax
---
```SQL
SELECT _column_name(s)_  
FROM _table_name_  
WHERE _column_name_ IN (_value1_, _value2_, ...);
```
### Example
---
Returnér alle `Customers` fra `Germany`, `France` eller `UK`:
```SQL
SELECT * FROM Customers  
WHERE Country IN ('Germany', 'France', 'UK');
```


## IN (SELECT)
---
`IN` kan bruges med en [[Subqueries|subquery]] i en [[WHERE Clause|WHERE]]-klausul.

Returnér alle `Customers` der har en ordre i `Orders`-[[Table|tabellen]]:
```SQL
SELECT * FROM Customers  
WHERE CustomerID IN (SELECT CustomerID FROM Orders);
```


## Related Topics
---
- [[WHERE Clause|WHERE]]
- [[SELECT]]
- 

## Resources
---
- [SQL In](https://www.w3schools.com/sql/sql_in.asp)
- 