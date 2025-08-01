tags: #Programmering #SQL

## Definition 
---
`FULL JOIN` returnerer alle rækker hvor der er et match i enten den venstre (``Customers``) eller højre (``Orders``) tabel. 

Hvis der ikke er noget match, bliver ``NULL`` returneret i de kolonner hvor der intet match er. 
Dette kan være i både den venstre og den højre tabel.
## Syntax
---
```sql
SELECT columns
FROM table1
FULL JOIN table2
ON table1.common_column = table2.common_column;
```
### Example
---
Retrieve all employees and their corresponding departments, including unmatched records from both [[Table|tables]]:
```sql
SELECT employees.first_name, employees.last_name, departments.department_name
FROM employees
FULL JOIN departments
ON employees.department_id = departments.department_id;
```


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
FULL JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

##### Result

| Name  | Product    |
| ----- | ---------- |
| John  | Laptop     |
| Sarah | Smartphone |
| Mike  | NULL       |
| NULL  | Tablet     |
Du får alle ``Customers`` og alle ``Orders``, uanset om de har et match.

## Related Topics
---
- [[Data Querying Overview]]
- [[Joins]]

## Resources
---
- [JOINS Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_17/scormcontent/index.html#/lessons/Xh1h5Fdn8KpTJAPPs09i5HcJfDfpkvGT)
- [SQL Full Join](https://www.w3schools.com/sql/sql_join_full.asp)