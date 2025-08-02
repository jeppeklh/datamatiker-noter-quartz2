tags: #Programmering #SQL #AdvancedTopicsSQL 

> [!tldr] Definition
> **Triggers** are special types of [[Stored Procedures|stored procedures]] that automatically execute in response to certain events on a particular [[Table|table]] or [[Views|view]]. 
> They are used for maintaining data integrity, enforcing business rules, and auditing changes.

---

## Syntax
```sql
CREATE TRIGGER trigger_name
AFTER INSERT | AFTER UPDATE | AFTER DELETE
ON table_name
FOR EACH ROW
BEGIN
    SQL statements;
END;
```

---

### Example
Create a trigger to log changes to the employee [[Table|table]]:
```sql
CREATE TRIGGER LogEmployeeChanges
AFTER UPDATE ON employees
FOR EACH ROW
BEGIN
    INSERT INTO EmployeeChanges (emp_id, old_salary, new_salary, change_date)
    VALUES (OLD.id, OLD.salary, NEW.salary, NOW());
END;
```

---

## Related Topics
- Link
- 

---

## Resources
- [SQL Triggers Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_24/scormcontent/index.html#/lessons/noo5pSf2wL0y6Phcuz4-w4iH2ZwuVMRN)
- 