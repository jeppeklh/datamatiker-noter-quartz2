tags: #Programmering #SQL #TCL #Statement 

> [!tldr] Definition
> A transaction is a sequence of one or more SQL operations treated as a single unit of work. 

A transaction ensures that either all operations are executed successfully or none at all, maintaining the integrity of the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]].

---

## Example
```sql
BEGIN TRANSACTION; 
-- SQL operations here 
COMMIT;
```

This begins a transaction and [[COMMIT|commits]] the changes if all operations are successful.

---

## Related Topics
- [[TCL Overview]]
- [[COMMIT]]
- [[ROLLBACK]]
- [[SAVEPOINT]]
- [[ACID]]

---

## Resources
- [Transactions Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_25/scormcontent/index.html#/lessons/IG1ZDoBjZ83eR45pigr3ww1zcGwU9JJD)
- 