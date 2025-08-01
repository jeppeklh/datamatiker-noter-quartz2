tags: #Programmering #SQL #TCL #Statement 

## Definition 
---
The `ROLLBACK` statement is used to undo all changes made during the current [[TRANSACTION|transaction]]. 

This ensures that if an error occurs, the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] can be restored to its previous state.
## Example
---
```sql
BEGIN TRANSACTION; 
UPDATE accounts SET balance = balance - 100 WHERE account_id = 1; 
UPDATE accounts SET balance = balance + 100 WHERE account_id = 2; 
-- Suppose an error occurs here 
IF error_condition THEN 
	ROLLBACK; 
END IF;
```

In this example, if an error occurs during the transfer of 100 units from account 1 to account 2, the `ROLLBACK` statement undoes all changes, ensuring the balances remain as they were before the [[TRANSACTION|transaction]] began.

## Related Topics
---
- [[TCL Overview]]
- [[TRANSACTION]]
- [[COMMIT]]
- [[SAVEPOINT]]
- [[ACID]]

## Resources
---
- Link
- 