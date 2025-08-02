tags: #Programmering #SQL #DataQuerying #Joins 

> [!tldr] Definition
> ``RIGHT JOIN`` returnerer alle rækker fra den tabel fra højresiden, og de matchene rækker fra den venstre tabel.

Hvis der ikke er noget match, bliver resultatet ``NULL`` på venstresiden.

---

## Syntax
```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.common_column = table2.common_column;
```

---

### Example
Retrieve all departments and their corresponding employees, including those without employees:
```sql
SELECT employees.first_name, employees.last_name, departments.department_name
FROM employees
RIGHT JOIN departments
ON employees.department_id = departments.department_id;
```

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

``RIGT JOIN`` returnerer alle rækker fra den tabel fra højresiden (``Orders``) og de matchene rækker fra den venstre tabel (``Customers``). Hvis der ikke er noget match, bliver resultatet ``NULL`` på venstresiden.

```SQL
SELECT Customers.Name, Orders.Product
FROM Customers
RIGHT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

##### Result

| Name  | Product    |
| ----- | ---------- |
| John  | Laptop     |
| Sarah | Smartphone |
| NULL  | Tablet     |
Ordren fra ``CustomerID = 4`` bliver altså returneret, selvom der ingen matchene ``Customer`` er. 
Dette bliver skrevet som ``NULL`` i ``Name`` kolonnen

---

## Related Topics
- [[Data Querying Overview]]
- [[Joins]]

---

## Resources
- [JOINS Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_17/scormcontent/index.html#/lessons/Xh1h5Fdn8KpTJAPPs09i5HcJfDfpkvGT)
- [SQL Right Join](https://www.w3schools.com/sql/sql_join_right.asp)