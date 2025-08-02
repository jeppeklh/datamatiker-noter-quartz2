tags: #Programmering #SQL #SQLSecurity

> [!tldr] Definition
> User Management in SQL involves creating, managing, and deleting user accounts that can access the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]].
> It includes assigning permissions to users to control what actions they can perform on the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]].

---

## Example
```sql
-- Creating a new user
CREATE USER 'username'@'hostname' IDENTIFIED BY 'password';

-- Granting privileges to a user
GRANT SELECT, INSERT, UPDATE ON database_name.* TO 'username'@'hostname';

-- Viewing user privileges
SHOW GRANTS FOR 'username'@'hostname';

-- Revoking privileges from a user
REVOKE INSERT ON database_name.* FROM 'username'@'hostname';

-- Deleting a user
DROP USER 'username'@'hostname';
```

---

## Related Topics
- [[GRANT]]
- [[REVOKE]]

---

## Resources
- Link
- 