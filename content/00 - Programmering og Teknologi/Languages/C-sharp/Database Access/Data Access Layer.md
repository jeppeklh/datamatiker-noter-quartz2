---
aliases:
  - DAL
---
tags: #C-sharp #Programmering #DatabaseAccess 

> [!tldr] Definition
> The Data Access Layer (DAL) is a crucial part of the application architecture that handles the interaction between the application and the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]]. 

It provides a set of [[Methods Overview|methods]] to perform [[CRUD Operations]]  without exposing the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] details to the rest of the application.

---

### Key Concepts
#### Abstraction
- The DAL abstracts the underlying [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] interactions, allowing the rest of the application to interact with the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] through a simplified API.
- This abstraction makes the application more modular and easier to maintain.

---

#### Reusability
- The DAL encapsulates common [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] operations into reusable methods. This reduces code duplication and ensures consistency in how [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] operations are performed.

---

#### Maintainability
- By isolating the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] access logic, any changes to the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] schema or queries can be managed in one place, making the application easier to maintain.

---

## Components of DAL
**1. Connection Management:**

- Manages the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] connections, ensuring they are opened and closed appropriately.
```csharp
public class DatabaseConnection
{
    private readonly string connectionString;

    public DatabaseConnection(string connectionString)
    {
        this.connectionString = connectionString;
    }

    public SqlConnection GetConnection()
    {
        return new SqlConnection(connectionString);
    }
}
```

**2. Data Access Methods:**

- Methods to perform [[CRUD Operations]].
```csharp
public class ProductRepository
{
    private readonly DatabaseConnection databaseConnection;

    public ProductRepository(DatabaseConnection connection)
    {
        databaseConnection = connection;
    }

    public List<Product> GetAllProducts()
    {
        using (var connection = databaseConnection.GetConnection())
        {
            connection.Open();
            var command = new SqlCommand("SELECT * FROM Products", connection);
            var reader = command.ExecuteReader();
            var products = new List<Product>();
            while (reader.Read())
            {
                products.Add(new Product
                {
                    Id = reader.GetInt32(0),
                    Name = reader.GetString(1),
                    Price = reader.GetDecimal(2)
                });
            }
            return products;
        }
    }
}
```

**3. Error Handling:**

- Handles [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]]-related errors and exceptions.
	- Ensures that errors are logged and managed appropriately without exposing them to the application user.

---

## Best Practices
**1. Use Parameterized Queries:**

- Protects against [[SQL Injection]] attacks.
```csharp
public Product GetProductById(int id)
{
    using (var connection = databaseConnection.GetConnection())
    {
        connection.Open();
        var command = new SqlCommand("SELECT * FROM Products WHERE Id = @Id", connection);
        command.Parameters.AddWithValue("@Id", id);
        var reader = command.ExecuteReader();
        if (reader.Read())
        {
            return new Product
            {
                Id = reader.GetInt32(0),
                Name = reader.GetString(1),
                Price = reader.GetDecimal(2)
            };
        }
        return null;
    }
}
```

**2. Connection Pooling:**

- Utilize connection pooling to manage [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] connections efficiently and improve performance.

**3. Transaction Management:**

- Manage transactions to ensure data consistency and integrity.
```csharp
public void UpdateProduct(Product product)
{
    using (var connection = databaseConnection.GetConnection())
    {
        connection.Open();
        using (var transaction = connection.BeginTransaction())
        {
            try
            {
                var command = new SqlCommand("UPDATE Products SET Name = @Name, Price = @Price WHERE Id = @Id", connection, transaction);
                command.Parameters.AddWithValue("@Name", product.Name);
                command.Parameters.AddWithValue("@Price", product.Price);
                command.Parameters.AddWithValue("@Id", product.Id);
                command.ExecuteNonQuery();
                transaction.Commit();
            }
            catch
            {
                transaction.Rollback();
                throw;
            }
        }
    }
}
```

---

## Related Topics
- [[Database Access Overview]]
- 

---

## Resources
- Link
- 