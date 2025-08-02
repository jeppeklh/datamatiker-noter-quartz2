tags: #Programmering #SQL #AdvancedTopicsSQL 

> [!tldr] Definition
> **Stored Procedures** er genanvendelige SQL-kodeblokke, der inkapsler forretningslogik, forbedrer ydeevne og øger sikkerheden.

---

## Syntax
```sql
CREATE PROCEDURE procedure_name
AS
BEGIN
    SQL statements;
END;
```

---

### Example
Create a stored procedure to update employee salaries:
```sql
CREATE PROCEDURE UpdateSalary
AS
BEGIN
    UPDATE employees
    SET salary = salary * 1.1
    WHERE performance = 'Excellent';
END;
```

---

## Execution
```SQL
CREATE PROCEDURE uspCreateCustomer
    @FirstName NVARCHAR(50),
    @LastName NVARCHAR(50),
    @Email NVARCHAR(50),
    @Address NVARCHAR(50),
    @City NVARCHAR(50),
    @Country NVARCHAR(50),
    @Points INT
AS
BEGIN
    INSERT INTO CUSTOMER(FirstName, LastName, Email, Address, City, Country, Points)
    VALUES(@FirstName, @LastName, @Email, @Address, @City, @Country, @Points)
END
```

```SQL
EXEC uspCreateCustomer
    @FirstName = 'John',
    @LastName = 'Doe',
    @Email = 'john.doe@example.com',
    @Address = '123 Main St',
    @City = 'New York',
    @Country = 'USA',
    @Points = 100;
```

---

## Related Topics
- [[Uge43 - Views & Stored Procedures|Views & Stored Procedures Opgaver]]
- [[Views]]

---

## Resources
- [Stored Procedures in SQL Server](https://dotnettutorials.net/lesson/sql-server-stored-procedure/)
- [Naming Conventions for Stored Procedures](https://www.mssqltips.com/sqlservertutorial/169/naming-conventions-for-sql-server-stored-procedures/)
- [Stored Procedure Video 1](https://www.youtube.com/watch?v=phy-UqRTsis&ab_channel=DatabaseStar)
- [Stored Procedure Video 2](https://www.youtube.com/watch?v=Kvrojn6UmE0&ab_channel=EducationisLife%28joedgoh%29)
- [Stored Procedures in C#](https://www.c-sharpcorner.com/article/execute-a-stored-procedure-programmatically/)


Skriv alle CRUD operationer for hver tabel i Stored Procedures
EXEC usp_StoredProcedureNavn 'Parameter';
