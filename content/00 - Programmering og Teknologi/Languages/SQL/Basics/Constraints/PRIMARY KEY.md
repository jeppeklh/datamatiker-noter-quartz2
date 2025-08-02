tags: #Programmering #SQL #SQLBasics #Constraint

> [!tldr] Definition
> The `PRIMARY KEY` constraint uniquely identifies each row in a [[Table]]. 
> Usually an ID.

A [[Table]] can have only one primary key, which can be a single column or a combination of multiple columns.

The primary key ensures that no two rows can have the same value for the primary key columns, and it also ensures that the primary key values are not `NULL`.

---

### Key Points
- A [[Table]] can have only one primary key.
- A primary key can be made up of a single column or multiple columns ([[Composite key]]).
- Primary keys enforce uniqueness and non-nullability.

---

## Syntax
```sql
CREATE TABLE table_name (
    column1 datatype PRIMARY KEY,
    column2 datatype,
    ...
);
```

---

### Example
```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    DateOfBirth DATE
);
```

In this example, `StudentID` is the primary key. 
Each student must have a unique `StudentID` value, and it cannot be `NULL`.

---

## Related Topics
- [[Constraints]]
- [[NOT NULL]]
- [[UNIQUE]]
- [[FOREIGN KEY]]
- [[CHECK]]
- [[DEFAULT]]

---

## Resources
- Link
- 