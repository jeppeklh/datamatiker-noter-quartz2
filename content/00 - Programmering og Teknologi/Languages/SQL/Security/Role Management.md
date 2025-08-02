tags: #Programmering #SQL #SQLSecurity

> [!tldr] Definition
> Role Management involves creating and managing roles, which are collections of privileges. 
> Roles make it easier to manage permissions for groups of users.

---

## Example
```sql
-- Creating a new role
CREATE ROLE 'role_name';

-- Granting privileges to a role
GRANT SELECT, INSERT ON database_name.* TO 'role_name';

-- Assigning a role to a user
GRANT 'role_name' TO 'username'@'hostname';

-- Revoking a role from a user
REVOKE 'role_name' FROM 'username'@'hostname';

-- Dropping a role
DROP ROLE 'role_name';
```

---

## Related Topics
- [[GRANT]]
- [[REVOKE]]

---

## Resources
- Link
- 