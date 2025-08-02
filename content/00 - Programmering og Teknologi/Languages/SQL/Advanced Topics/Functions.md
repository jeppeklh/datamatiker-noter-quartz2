tags: #Programmering #SQL #AdvancedTopicsSQL 

> [!tldr] Definition
> **Functions** are similar to [[Stored Procedures|stored procedures]] but can return a single value and can be used in SQL statements. 
>They are used for computations and returning a single value.

---

## Syntax
```sql
CREATE FUNCTION function_name (parameters)
RETURNS return_datatype
AS
BEGIN
    SQL statements;
    RETURN value;
END;
```

---

### Example
Create a function to calculate the annual salary:
```sql
CREATE FUNCTION CalculateAnnualSalary (monthly_salary DECIMAL)
RETURNS DECIMAL
AS
BEGIN
    RETURN monthly_salary * 12;
END;
```

---

## Related Topics
- Link
- 

---

## Resources
- Link
- 