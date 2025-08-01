	tags: #Programmering #SQL #SQLBasics #Constraint

## Definition 
---
En fremmednøgle (en: foreign key – FK) er en kopi af en [[PRIMARY KEY|primærnøgle]] (også hvis den er [[Composite key|sammensat]]) fra en anden [[Relationer|relation]] (i sjældne tilfælde fra samme relation), der fungerer som reference fra rækker i relationen, den indgår i, til en unik række i relationen med primærnøglen.

En [[Relationer|relation]] kan indeholde nul til flere fremmednøgler, og når de er fundet for en relation, skal de også udtrykkes i relationsskemaet:

A `FOREIGN KEY` is a column or a set of columns in a [[Table]] that establishes a link between the data in two [[Table|tables]]. 

The foreign key in the referencing [[Table]] (child [[Table]]) points to the [[PRIMARY KEY|primary key]] or a unique key in the referenced [[Table]] (parent [[Table]]). 

A foreign key could be a studentName, where a [[PRIMARY KEY|primary key]] could be studentID

This ensures referential integrity, meaning that the value in the foreign key column must exist in the  [[PRIMARY KEY|primary key]] column of the parent [[Table]].

### Key Points
---
- A [[Table]] can have multiple foreign keys.
- A foreign key can reference a [[PRIMARY KEY|primary key]] or a unique key in another [[Table]].
- Foreign keys help maintain consistency and integrity in the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database]] by ensuring that relationships between [[Table|tables]] remain valid.
## Syntax
---
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    FOREIGN KEY (column1) REFERENCES other_table (column_name)
);
```
### Example
---
Consider a `Courses` [[Table]] and an `Enrollments` [[Table]]:
```sql
CREATE TABLE Courses (
    CourseID INT PRIMARY KEY,
    CourseName VARCHAR(100)
);

CREATE TABLE Enrollments (
    EnrollmentID INT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);
```

In this example:

- `StudentID` in the `Enrollments` [[Table]] is a foreign key that references the `StudentID` in the `Students` [[Table]].
- `CourseID` in the `Enrollments` [[Table]] is a foreign key that references the `CourseID` in the `Courses` [[Table]].

This setup ensures that any `StudentID` in the `Enrollments` [[Table]] must exist in the `Students` [[Table]], and any `CourseID` in the `Enrollments` [[Table]] must exist in the `Courses` [[Table]], maintaining referential integrity.


## Fremmednøgle i SQL notation
---
### Syntax
---

```SQL
NavnPåForeignKey Int NOT NULL FOREIGN KEY REFERENCES TableForeignKeyenKommerFra(PrimærNøgleenFraDetTable)
```

### Eksempel
---
```SQL
CREATE TABLE PARTICIPANT (
  Email NVarChar(50) PRIMARY KEY,
  FirstName NVarChar(30) NOT NULL,
  LastName NVarChar(40) NOT NULL,
  ImagePath NVarChar(100) NOT NULL,
  SemesterId Int NOT NULL FOREIGN KEY REFERENCES SEMESTER(SemesterId)
);

```


## Related Topics
---
- [[Constraints]]
- [[NOT NULL]]
- [[UNIQUE]]
- [[PRIMARY KEY]]
- [[CHECK]]
- [[DEFAULT]]

## Resources
---
- Link
- 