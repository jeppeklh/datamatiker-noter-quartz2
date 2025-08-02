tags: #Programmering #SQL #DataQuerying #Joins

> [!tldr] Definition
> **Left Join** retrieves all records from the left [[Table|table]] and the matched records from the right [[Table|table]]. 
> If there is no match, the result is NULL from the right [[Table|table]].

---

## Syntax
```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.common_column = table2.common_column;
```

---

### Example
```sql
SELECT Customers.Name, Orders.Product 
FROM Customers 
LEFT JOIN Orders 
ON Customers.CustomerID = Orders.CustomerID;
```
This returns **all customers**, including those who have not placed any orders (with `NULL` in `Orders.Product` for those who haven't).

```SQL
SELECT Orders.Product, Customers.Name
FROM Orders
LEFT JOIN Customers
ON Orders.CustomerID = Customers.CustomerID;
```
This returns **all orders**, including those that don't have a corresponding customer (with `NULL` in `Customers.Name` if no customer exists).

---

### Example 2 - with output
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
LEFT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

##### Result

| **Name** | **Product** |
| -------- | ----------- |
| John     | Laptop      |
| Sarah    | Smartphone  |
| Mike     | NULL        |
Mike dukker selvom han ikke har placeret en ordre, med `NULL`i product kollonnen.

---

## Related Topics
- [[Data Querying Overview]]
- [[Joins]]

---

## Resources
- [JOINS Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_17/scormcontent/index.html#/lessons/Xh1h5Fdn8KpTJAPPs09i5HcJfDfpkvGT)
- [SQL Left Join](https://www.w3schools.com/sql/sql_join_left.asp)