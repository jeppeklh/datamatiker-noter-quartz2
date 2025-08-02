tags: #Programmering #SQL #DCL #Statement 

> [!tldr] Definition
> The `GRANT` statement is used to give specific privileges to users or roles in the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]]. 

This can include permissions such as [[SELECT]], [[INSERT]], [[UPDATE]], [[DELETE]], and more.

---

## Example
```sql
GRANT SELECT, INSERT ON Employees TO user1;
```
This command grants the [[SELECT]] and [[INSERT]] privileges on the `Employees` [[Table|table]] to `user1`.

---

## Related Topics
- [[DCL Overview]]
- [[REVOKE]]

---

## Resources
- Link
- 