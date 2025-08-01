tags: #Programmering #SQL #DataQuerying #Joins

## Definition 
---
``INNER JOIN`` returnerer kun rækkerne hvor der er et match i begge [[Table|tabeller]].
## Syntax
---
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.common_column = table2.common_column;
```
### Example
---
```sql
SELECT Customers.Name, Orders.Product
FROM Customers
INNER JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

- **`SELECT Customers.Name, Orders.Product`** 
  Jeg vil have ``Name`` fra ``Customers`` tabellen og ``Product`` fra ``Orders`` tabellen.

- **`FROM Customers`**
  Start med at kigge på ``Customers`` tabellen.
  
- **`INNER JOIN Orders`**
  Join ``Orders`` tabellen med ``Customers`` tabellen, men inkluder kun rækker hvor conditionen nedenunder er sand.

- **`ON Customers.CustomerID = Orders.CustomerID`**
  ``CustomerID`` i ``Customers`` tabellen SKAL være lig med ``CustomerID`` i ``Orders`` tabellen.


Tabellerne der bliver skrevet efter ``FROM`` og ``INNER JOIN`` (altså hvilken tabel der bliver joinet på hvilken tabel) kan byttes om. Det betyder ikke noget i ``INNER JOIN``. Det betyder dog noget i [[Left Join]] og [[Right Join]].


### Example - with output
---
- **Customers**:

|CustomerID|Name|
|---|---|
|1|John|
|2|Sarah|
|3|Mike|

- **Orders**:

| OrderID | CustomerID | Product    |
| ------- | ---------- | ---------- |
| 101     | 1          | Laptop     |
| 102     | 2          | Smartphone |
| 103     | 4          | Tablet     |
```SQL
SELECT Customers.Name, Orders.Product
FROM Customers
INNER JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

##### Result

|Name|Product|
|---|---|
|John|Laptop|
|Sarah|Smartphone|
Kun ``Customers`` med matchene ``Orders`` bliver returneret. 
Mike og ordren med ``CustomerID = 4`` bliver ikke vist, fordi de begge intet match har.

## Related Topics
---
- [[Data Querying Overview]]
- [[Joins]]

## Resources
---
- [JOINS Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_17/scormcontent/index.html#/lessons/Xh1h5Fdn8KpTJAPPs09i5HcJfDfpkvGT)
- [SQL Inner Join](https://www.w3schools.com/sql/sql_join_inner.asp)