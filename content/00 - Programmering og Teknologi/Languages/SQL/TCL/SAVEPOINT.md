tags: #Programmering #SQL #TCL #Statement 

## Definition 
---
The `SAVEPOINT` statement sets a point within a [[TRANSACTION|transaction]] to which you can later roll back. 
This allows for partial [[ROLLBACK|rollback]] within a [[TRANSACTION|transaction]].
## Example
---
```sql
SAVEPOINT savepoint_name; 
-- SQL operations here 
ROLLBACK TO savepoint_name;
```

This command sets a savepoint and later rolls back to it.
## Related Topics
---
- [[TCL Overview]]
- [[TRANSACTION]]
- [[COMMIT]]
- [[ROLLBACK]]
- [[ACID]]

## Resources
---
- Link
- 