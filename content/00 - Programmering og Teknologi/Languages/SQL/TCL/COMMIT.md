tags: #Programmering #SQL #TCL #Statement 

## Definition 
---
The `COMMIT` statement is used to save all changes made during the current [[TRANSACTION|transaction]]. 

Once a commit is issued, the changes are permanent and visible to other users.
## Example
---
```sql
BEGIN TRANSACTION; 
UPDATE accounts SET balance = balance - 100 WHERE account_id = 1; 
UPDATE accounts SET balance = balance + 100 WHERE account_id = 2; 
COMMIT;
```

This example transfers 100 units from account 1 to account 2. 
If both updates are successful, the changes are saved permanently with the `COMMIT` statement.

## Related Topics
---
- [[TCL Overview]]
- [[TRANSACTION]]
- [[ROLLBACK]]
- [[SAVEPOINT]]
- [[ACID]]

## Resources
---
- Link
- 