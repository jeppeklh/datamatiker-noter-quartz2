tags: #Programmering #SQL

## Definition 
---
`NOT` operatoren bruges i kombination med andre operationer til at give det modsatte resultat.
## Syntax
---
```SQL
SELECT _column1_, _column2, ..._  
FROM _table_name_  
WHERE NOT _condition_;
```
### Example
---
Vælg kun de `Customers` der IKKE er fra Spanien
```SQL
SELECT * FROM Customers  
WHERE NOT Country = 'Spain';
```


## NOT + andre operationer eksempler
---
#### NOT LIKE
Vælg `Customers` der ikke starter med A.
```SQL
SELECT * FROM Customers  
WHERE CustomerName NOT LIKE 'A%';
```

#### NOT BETWEEN
Vælg `Customers` med et ID der IKKE er imellem 10 og 60
```SQL
SELECT * FROM Customers  
WHERE CustomerID NOT BETWEEN 10 AND 60;
```

#### NOT IN
Vælg `Customers` der ikke er fra Paris eller London
```SQL
SELECT * FROM Customers  
WHERE City NOT IN ('Paris', 'London');
```

## Related Topics
---
- [[SELECT]]
- [[WHERE Clause|WHERE]]
- [[LIKE Operator|LIKE]]
- [[BETWEEN Operator|Between]]
- [[IN Operator|IN]]

## Resources
---
- Link
- 