tags: #Programmering #SQL #Database #ACID

> [!tldr] Definition
> ACID is an acronym for the four properties that ensure reliable processing of [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|databse]] transactions: **Atomicity**, **Consistency**, **Isolation**, and **Durability**. 

These properties guarantee that transactions are processed reliably and help maintain data integrity.

The ACID properties are crucial for [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|datavase]] systems, especially in environments requiring high reliability and integrity, such as banking, e-commerce, and other transactional systems. They help prevent data corruption and ensure data remains accurate and consistent.

---

#### Atomicity
Atomicity ensures that each transaction is treated as a single unit, which either succeeds completely or fails completely. 

If any part of the transaction fails, the entire transaction is rolled back, leaving the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] in its previous state.

##### Example 
If a transaction involves transferring money from one bank account to another, both the debit and credit operations must succeed. 
If the debit operation fails, the credit operation must not proceed, and vice versa.

---

#### Consistency
If we perform any operation over the data, its value before and after the operation should be preserved. 
##### Example
The account balance before and after the transaction should be correct, i.e., it should remain conserved.

---

#### Isolation
Isolation ensures that concurrent transactions do not interfere with each other. 
Each transaction is executed in isolation from other transactions, meaning that its intermediate states are invisible to other transactions.

##### Example
If two transactions are simultaneously updating the same data, isolation ensures that the changes made by one transaction are not visible to the other until they are committed.

---

#### Durability
Durability ensures that once a transaction is committed, it remains in the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] even in the event of a system failure. 
This guarantees that the data is permanently recorded.

##### Example
After a transaction commits a change, like updating an account balance, the update must be permanently stored and recoverable even if the system crashes immediately afterward.

---

## Related Topics
- [[TCL Overview]]
- 

---

## Resources
- Link
- 