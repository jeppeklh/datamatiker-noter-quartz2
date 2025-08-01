tags: #Programmering #SQL #SQLSecurity 

## Definition 
---
Data Encryption in SQL ensures that the data stored in the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] is secure and protected from unauthorized access. 
It involves encrypting data at rest (stored data) and in transit (data being transferred).
## Example
---
```sql
-- Encrypting a column in MySQL using AES_ENCRYPT
INSERT INTO table_name (column1, encrypted_column)
VALUES ('data', AES_ENCRYPT('data_to_encrypt', 'encryption_key'));

-- Decrypting a column in MySQL using AES_DECRYPT
SELECT column1, AES_DECRYPT(encrypted_column, 'encryption_key')
FROM table_name;

-- Enabling SSL for MySQL connections
-- Edit the MySQL configuration file (my.cnf or my.ini)
[mysqld]
ssl-ca=/path/to/ca-cert.pem
ssl-cert=/path/to/server-cert.pem
ssl-key=/path/to/server-key.pem

-- Restart MySQL server
sudo service mysql restart

-- Connecting to MySQL with SSL
mysql -u username -p --ssl-ca=/path/to/ca-cert.pem --ssl-cert=/path/to/client-cert.pem --ssl-key=/path/to/client-key.pem
```

## Related Topics
---
- Link
- 

## Resources
---
- Link
- 