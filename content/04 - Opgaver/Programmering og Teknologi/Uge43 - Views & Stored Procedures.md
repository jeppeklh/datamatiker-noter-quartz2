tags: #C-sharp #Programmering


Du har allerede arbejdet grundigt med database-design i Fase A, hvor du udviklede en UML-database model og normaliserede dine data. I Fase B omsatte du dette design til en fungerende database ved at oprette tabeller gennem SQL's Data Definition Language (DDL) og manipulere data med Data Manipulation Language (DML). Du har også arbejdet med Data Query Language (DQL) til at forespørge databasen, analysere og hente data.  
I dag kommer du til at arbejde med Views og Stored Procedures for webshop-databasen. Øvelserne er organiseret i forhold til at sikre forståelse af begreberne og derefter arbejde med praktiske implementeringer i databasen. Til sidst bliver der inkluderet en C#-øvelse for at demonstrere, hvordan man interagerer med views og stored procedures via kode.

## Øvelse 1: Terminologi
---
**_Forventning_:** At sikre, at du har en klar forståelse af de grundlæggende begreber inden for Views og Stored Procedures, som er nødvendige for at arbejde effektivt med databaser.

Brug "Ordet rundt" til at reflektere over begreberne:

##### Forklar begrebet View i SQL. Hvordan adskiller et view sig fra en almindelig tabel?
---
Et [[Views|view]] er en virtuel [[Table|tabel]] baseret på en forespørgsel, der viser [[Data|data]] fra andre tabeller uden selv at gemme data. 
I modsætning til en tabel, der lagrer data, viser et view kun resultaterne af en forespørgsel.
##### Hvad er formålet med et View?
---
Formålet er at forenkle komplekse forespørgsler, øge datasikkerheden ved at begrænse adgang, og gøre ofte anvendte forespørgsler nemmere at genbruge.
##### Forklar begrebet Stored Procedure og diskutere fordelene ved den.
---
En gemt SQL-forespørgsel, der kan køres gentagne gange. 
Fordelene er bedre performance, genbrug af kode og øget sikkerhed.
##### Hvornår bør du bruge en Stored Procedure frem for at skrive forespørgsler direkte i applikationskoden?
---
Brug Stored Procedures for kompleks logik, højere sikkerhed, forbedret performance og når koden skal genbruges flere steder.

## Øvelse 2: Views
---
**_Forventning_**: At oprette views, der forenkler adgangen til ofte anvendte forespørgsler og bruge dem til at udtrække data fra databasen på en effektiv måde.

Udfør følgende på Microsoft SQL Server Management Studio:

##### 2.1 Opret et View for Kunder med Points
---
Opret et view kaldet vwCustomerPoints, som viser CustomerID, FirstName, LastName, City, Country, og Points fra CUSTOMER tabellen.
```SQL
CREATE VIEW vwCustomerPoints AS
SELECT customerID, CONCAT(FirstName, ' ', LastName) as customerName, Email, Points, telephone, customer_address
FROM Customers;
```

Brug dette view til at hente alle kunder, der har optjent over 300 points.
```SQL
SELECT * FROM vwCustomerPoints WHERE points > 300;
```

##### 2.2 Opret et View for Ordrer og Kundens Information
---
Opret et view kaldet vwOrderCustomer, som kombinerer oplysninger fra ORDER og CUSTOMER tabellerne. Viewet skal indeholde OrderID, OrderDate, CustomerName (kombination af FirstName og LastName), City, og TotalPrice (summen af Price gange Quantity fra ORDERITEM).
```SQL
CREATE VIEW vwOrderCustomer AS
SELECT s.OrderID, s.OrderDate, CONCAT(c.FirstName, ' ', c.LastName) AS CustomerName, c.City, SUM(o.Price * o.Price) AS TotalPrice
FROM SHOPPINGCART s
JOIN CUSTOMER c ON s.CustomerID = c.CustomerID
LEFT JOIN ORDERITEM o ON o.OrderID = s.OrderID
GROUP BY s.OrderID, s.OrderDate, c.FirstName, c.LastName, c.City
```

Brug viewet til at finde alle ordrer, som er blevet afgivet af kunder, der bor i "København".
```SQL
SELECT * FROM vwOrderCustomer
Where City Like '%København%';
```
##### 2.3 Opret et View for Produkter med Lav Beholdning
---
Opret et view kaldet vwLowStockProducts, som viser alle produkter fra PRODUCT tabellen, hvor StockQuantity er mindre end 3.
```SQL
CREATE VIEW vwLowStockProducts AS
SELECT *
FROM PRODUCT
WHERE StockQuantity < 3;
```

Brug viewet til at hente alle produkter, der har "Telefon" i navnet.
```SQL
SELECT * FROM vwLowStockProduct
WHERE ProductName Like '%Telefon%';
```

## Øvelse 3: Stored Procedures
---
**_Forventning_**: At oprette og opdatere stored procedures, der udfører specifikke operationer i databasen.  

Udfør følgende på Microsoft SQL Server Management Studio:

##### 3.1 Opret en stored procedure kaldet uspCreateCustomer, der tager FirstName, LastName, Email, Address, City, Country, og Points som parametre, og indsætter en ny kunde i CUSTOMER tabellen.
---
```SQL
CREATE PROCEDURE uspCreateCustomer
    @FirstName NVARCHAR(50),
    @LastName NVARCHAR(50),
    @Email NVARCHAR(50),
    @Address NVARCHAR(50),
    @City NVARCHAR(50),
    @Country NVARCHAR(50),
    @Points INT
AS
BEGIN
    INSERT INTO CUSTOMER(FirstName, LastName, Email, Address, City, Country, Points)
    VALUES(@FirstName, @LastName, @Email, @Address, @City, @Country, @Points)
END
```
##### 3.2 Ændre uspCreateCustomer til også at returnere CustomerID for den nyoprettede kunde. Dette kan gøres ved hjælp af SCOPE_IDENTITY().
---
```SQL
CREATE PROCEDURE uspCreateCustomer
    @FirstName NVARCHAR(50),
    @LastName NVARCHAR(50),
    @Email NVARCHAR(50),
    @Address NVARCHAR(100),
    @City NVARCHAR(50),
    @Country NVARCHAR(50),
    @Points INT
AS
BEGIN
  INSERT INTO CUSTOMER(FirstName, LastName, Email, Address, City, Country, Points)
    VALUES(@FirstName, @LastName, @Email, @Address, @City, @Country, @Points)
    SELECT SCOPE_IDENTITY() AS CustomerID;
END
```
##### 3.3 Opret en stored procedure kaldet uspGetCustomerOrders, der tager CustomerID som parameter og returnerer alle ordrer for den specifikke kunde fra SHOPPINGCART (ORDER) tabellen.
---
```SQL
CREATE PROC uspGetCustomerOrders
    @CustomerID INT
AS
BEGIN
    SELECT *
    FROM SHOPPINGCART s
    Where s.CustomerID = @CustomerID    
END
```
##### 3.4 Ændre uspGetCustomerOrders til også at returnere produktdetaljer for hver ordre ved hjælp af JOIN med ORDERITEM og PRODUCT.
---
```SQL
CREATE PROCEDURE uspGetCustomerOrders
    @CustomerID INT
AS
BEGIN
	SELECT oi.OrderID, p.ProductName, oi.Quantity, SUM(oi.Price * oi.Quantity)
    FROM SHOPPINGCART s
    JOIN ORDERITEM oi ON s.OrderID = s.OrderID
    JOIN PRODUCT p ON p.ProductID = oi.ProductID
    Where s.CustomerID = @CustomerID  
    GROUP BY oi.OrderID, p.ProductName, oi.Quantity, oi.Price, oi.Quantity
END
```
##### 3.5 Opret en stored procedure kaldet uspUpdateCustomerPoints, der tager OrderID som parameter, beregner kundens optjente point (10 % af den totale ordrepris, afrundet), og opdaterer kundens point i CUSTOMER-tabellen.  
---
```SQL
 CREATE PROC uspUpdateCustomerPoints
    @OrderID INT
AS
BEGIN
    DECLARE @PointsEarned DECIMAL;
    DECLARE @CustomerID INT;

    SELECT @CustomerID = c.CustomerID,
           @PointsEarned = SUM(oi.Price * oi.Quantity) * 0.1
    FROM CUSTOMER c
    JOIN SHOPPINGCART s ON c.CustomerID = s.CustomerID
    JOIN ORDERITEM oi ON s.OrderID = oi.OrderID
    WHERE s.OrderID = @OrderID
    GROUP BY c.CustomerID;

    UPDATE CUSTOMER
    SET Points = Points + @PointsEarned 
    WHERE CustomerID = @CustomerID;
END;
```

## Øvelse 4: Brug Views og Stored Procedures i C-Sharp
---
**_Forventning_**: At få praktisk erfaring med at bruge views og stored procedures i en C#-applikation.

##### 4.1 Kald stored procedure uspCreateCustomer fra din C#-applikation til at oprette nye kunder i systemet.
---
Bare hakket i Main metoden

```csharp
  // Named pipe connection string for LocalDB
  string connectionString = @"Server=np:\\.\pipe\LOCALDB#9D20B01A\tsql\query;Database=WepshopDatabase;Integrated Security=true;";

  Console.WriteLine("Enter Firstname: ");
  string firstname = Console.ReadLine();

  Console.WriteLine("Lastname: ");
  string lastname = Console.ReadLine();

  Console.WriteLine("Email: ");
  string email = Console.ReadLine();

  Console.WriteLine("Address: ");
  string address = Console.ReadLine();

  Console.WriteLine("City: ");
  string city = Console.ReadLine();

  Console.WriteLine("Country: ");
  string country = Console.ReadLine();

  Console.WriteLine("Points: ");
  int points = int.Parse(Console.ReadLine());

  using (SqlConnection connection = new SqlConnection(connectionString))
  {
      connection.Open();
      SqlCommand sql_cmnd = new SqlCommand("uspCreateCustomer", connection);
      sql_cmnd.CommandType = CommandType.StoredProcedure;
      sql_cmnd.Parameters.AddWithValue("@FirstName", SqlDbType.NVarChar).Value = firstname;
      sql_cmnd.Parameters.AddWithValue("@LastName", SqlDbType.NVarChar).Value = lastname;
      sql_cmnd.Parameters.AddWithValue("@Email", SqlDbType.NVarChar).Value = email;
      sql_cmnd.Parameters.AddWithValue("@Address", SqlDbType.NVarChar).Value = address;
      sql_cmnd.Parameters.AddWithValue("@City", SqlDbType.NVarChar).Value = city;
      sql_cmnd.Parameters.AddWithValue("@Country", SqlDbType.NVarChar).Value = country;
      sql_cmnd.Parameters.AddWithValue("@Points", SqlDbType.Int).Value = points;
      sql_cmnd.ExecuteNonQuery();
      connection.Close();

  }
          
```
##### 4.2 Brug vwCustomerPoints View i din C#-applikation til at udskrive en liste over alle kunder, der har optjent over 300 points.  
---
```csharp
 using (SqlConnection connection = new SqlConnection(connectionString))
 {
     connection.Open();

     // Using SqlCommand to select from the view
     SqlCommand sql_cmnd = new SqlCommand("SELECT * FROM vwCustomerPoints WHERE points > 300", connection);
     using (SqlDataReader dataReader = sql_cmnd.ExecuteReader())
     {
         // Read and display customer points
         while (dataReader.Read())
         {
             Console.WriteLine("Customer: {0}, Points: {1}", dataReader["CustomerName"], dataReader["Points"]);
         }
     }
 }
```

## Øvelse 5: Vidensdeling kl. 14:30
---
**_Forventning_**: At evaluere, hvad du har lært om Views og Stored Procedures, og diskutere de fordele og ulemper, som disse teknologier tilbyder.

·        Reflektér over arbejdet med views og stored procedures. Hvilke fordele har de givet i forhold til almindelige SQL-forespørgsler?

·        Præsenter din løsning fra øvelserne. Hvordan brugte du stored procedures, og hvilken fordel gav det i din applikation?

_Tidsramme: **30** minutter_

## Related Topics
---
- [[Views]]
- [[Stored Procedures]]
## Resources
---
- Link
- 