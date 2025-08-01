tags: #Programmering #SQL #DCL #Statement 

## Definition 
---
The `REVOKE` statement is used to remove specific privileges from users or roles in the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]]. This ensures that access can be controlled and restricted as needed.

## Example
---
```sql
REVOKE SELECT, INSERT ON Employees FROM user1
```
This command revokes the [[SELECT]] and [[INSERT]] privileges on the `Employees` [[Table|table]] from `user1`.


## Related Topics
---
- [[DCL Overview]]
- [[GRANT]]

## Resources
---
- Link
- 