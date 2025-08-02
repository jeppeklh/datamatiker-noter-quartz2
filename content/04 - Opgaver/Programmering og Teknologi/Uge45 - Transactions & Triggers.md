  
Dette opgavesæt giver dig mulighed for at oprette og arbejde med transaktioner med stored procedures samt skabe triggers i en webshop-database. Formålet er at styrke dine færdigheder i SQL Server ved at anvende både transaktioner og triggers til automatisering af opgaver, sikring af dataintegritet og implementering af forretningslogik.


---

## Øvelse 1: Terminologi
**_Forventning_:** At forstå grundlæggende begreber inden for transaktioner og triggers.

Brug "Ordet rundt" til at reflektere over begreberne:

##### Hvad er en transaktion i SQL, og hvorfor er den vigtig i databaseadministration?
En transaktion er en sekvens af operationer, som behandles som en enkelt logisk enhed. 
Det er vigtigt i databaseadministration for at sikre dataintegritet, især når flere relaterede ændringer skal gennemføres sammen eller slet ikke (som ved opdatering af lagerbeholdning, betaling og ordrestatus samtidigt).
Hvis en af de operationer fejler, skal de andre også annulleres.
##### Hvilke egenskaber definerer ACID for en transaktion, og hvad står hver af dem for?
- **Atomicity**: Sikrer, at alle operationer inden for en transaktion er afsluttede; hvis én fejler, rulles transaktionen tilbage.
- **Consistency**: Sikrer, at databasen forbliver i en gyldig tilstand både før og efter transaktionen.
- **Isolation**: Sikrer, at hver transaktion behandles osm en enkelt operation, så de ikke forstyrrer hinanden.
- **Durability**: Garanterer, at resultaterne af en bekræftet transaktion permanent gemmes i databasen.

##### Hvad er en trigger, og hvordan adskiller den sig fra en stored procedure?
**Trigger**
Udføres automatisk som svar på specifikke hændelser (f.eks. [[INSERT]], [[UPDATE]]) på en [[Table|tabel]].
Triggers kan heller ikke modtage parametre.
I en trigger kan [[TRANSACTION|transaktioner]] hverken [[COMMIT|forpligtes]] eller [[ROLLBACK|rulles tilbage]].

**[[Stored Procedures|Stored Procedure]]**
En præ-skrevet række SQL-kommandoer, som skal udføres manuelt.

##### Forklar forskellen mellem de tre typer af triggers i SQL Server: DML, DDL, og Logon triggers.
**DML Triggers**
Udløses af ændringer i data ([[INSERT]], [[UPDATE]], [[DELETE]]).

**DDL Triggers**
Reagerer på ændringer i skemaet/[[Table|table]] ([[CREATE TABLE|CREATE]], [[ALTER TABLE|ALTER]], [[DROP TABLE|DROP]]).

**Logon Triggers**
Aktiveres, når en bruger logger ind, ofte til sikkerhedslogning.

##### Forklar forskellen mellem de AFTER og INSTEAD OF triggers i SQL Server.
**AFTER Triggers**
Udføres efter den udløsende handling er fuldført.

**INSTEAD OF Triggers**
Udføres i stedet for den specificerede handling og muliggør tilpasset logik.

---

## Øvelse 2: Transaktioner i praksis
**_Forventning_**: Få praktisk erfaring med brug af transaktioner og stored procedures til at sikre dataintegritet i en webshop-database.

Du skal oprette tre stored procedures til at håndtere følgende processer: oprettelse af en ny ordre (shopping cart), indsættelse af produkter i ordrelinjerne, og opdatering af lagerbeholdningen. Derefter skal du bruge disse stored procedures i én samlet transaktion, som sikrer, at alle ændringer kun gemmes, hvis alle operationer er gennemført uden fejl.

---

#### Øvelse 2.1: Opret en stored procedure til oprettelse af en ordre (SHOPPINGCART)

Opret en stored procedure kaldet uspCreateOrder, der:
- Indsætter en ny post i SHOPPINGCART-tabellen.
- Returnerer det nye OrderID via et output-parameter, så det kan bruges i næste øvelse.

```SQL
CREATE PROC uspCreateOrder
	@CUSTOMERID INT,
	@ORDERDATE DATETIME2,
	@POINTSUSED INT,
	@ORDERSTATUSID INT,
	@PAYMENTMETHODID INT,
	@ORDERID INT OUTPUT
AS
BEGIN
	INSERT INTO SHOPPINGCART 
	VALUES(@CUSTOMERID, @ORDERDATE, @POINTSUSED, @ORDERSTATUSID, @PAYMENTMETHODID)
	SET @ORDERID = SCOPE_IDENTITY();
END;
```
---

#### Øvelse 2.2: Opret en stored procedure til indsættelse af ordrelinjer (ORDERITEM)
Opret en stored procedure kaldet uspCreateOrderItem, der:
- Tilføjer produkter til ORDERITEM-tabellen med referencen til OrderID fra øvelse 2.1.
```SQL
CREATE PROCEDURE uspCreateOrderItem 
    @orderID INT,
    @productID INT,
    @amount INT,
    @sumPrice FLOAT
AS
BEGIN
    INSERT INTO Product_Orders (order_id, product_id, amount, sum_price)
    VALUES (@orderID, @productID, @amount, @sumPrice);
END;
```

Den kan så kaldes således: 
```SQL
DECLARE @ORDERID INT  
EXEC uspCreateOrder 4, '2031-12-01', 1, 1, 1, @ORDERID OUTPUT  
EXEC uspCreateOrderItem @ORDERID, 1, 666, 123, 1
```
---

#### Øvelse 2.3: Opret en stored procedure til opdatering af lagerbeholdningen (PRODUCT)
Opret en stored procedure kaldet uspUpdateStockQuantity, der:
- Opdatere lagerbeholdningen for et produkt med en given mængde.
- Tjekker, at der stadig er nok produkter på lager; hvis lageret går i minus, skal opdateringen annulleres.
- Returnerer en statuskode eller en besked som output for at indikere, om operationen var succesfuld eller mislykket.
```SQL
CREATE PROCEDURE uspUpdateStockQuantity 
    @productID INT,
    @amount INT,
    @statusMessage NVARCHAR(50) OUTPUT
AS
BEGIN
    DECLARE @currentStock INT;

    SELECT @currentStock = in_stock FROM Products WHERE product_id = @productID;

    IF (@currentStock < @amount)
    BEGIN
        SET @statusMessage = 'Insufficient stock';
        RETURN;
    END

    UPDATE Products
    SET in_stock = in_stock - @amount
    WHERE product_id = @productID;

    SET @statusMessage = 'Stock updated successfully';
END;
```

---

#### Øvelse 2.4: Brug stored procedures i en transaktion
Opret en transaktion i SQL Server, der kalder de tre stored procedures fra trin 2.1 til 2.3:
- Start transaktionen med BEGIN [[TRANSACTION]].
- Kald uspCreateOrder, uspCreateOrderItem, og uspUpdateStockQuantity i rækkefølge.
- Brug output-parametre til at kontrollere, om hver procedure er gennemført uden fejl.
- Hvis en af procedurerne mislykkes (f.eks. på grund af lav lagerbeholdning), skal transaktionen annulleres med [[ROLLBACK]].
- Hvis alle procedurer gennemføres uden fejl, afsluttes transaktionen med [[COMMIT]].
```SQL
DECLARE @ORDERID INT, @STATUSMESSAGE NVARCHAR(50);
BEGIN TRANSACTION
EXEC uspCreateOrder 4, '2024-11-05', 1, 1, 1, @ORDERID OUTPUT
EXEC uspCreateOrderItem @ORDERID, 1, 10, 20, 1
EXEC uspUpdateStockQuantity 4, 1, @STATUSMESSAGE OUTPUT

IF @ORDERID = 0
BEGIN
	ROLLBACK TRANSACTION;
	PRINT 'Transaction rolled back due to Order not found'
END

ELSE IF @statusMessage = 'Insufficient stock'
BEGIN
    ROLLBACK TRANSACTION;
    PRINT 'Transaction rolled back due to insufficient stock.';
END

ELSE
BEGIN
    COMMIT TRANSACTION;
    PRINT 'Transaction committed successfully.';
END;
```

---

#### Øvelse 2.5: Refleksion over Transaktioner
Skriv dine refleksioner over følgende spørgsmål:
##### Hvorfor er det vigtigt at bruge både BEGIN TRANSACTION, COMMIT, og ROLLBACK i ovenstående transaktion?
Brug af BEGIN [[TRANSACTION]], [[COMMIT]] og [[ROLLBACK]] er kritisk for atomaritet og konsistens, hvilket sikrer, at alle ændringer enten sker samlet eller slet ikke.
##### Hvordan sikrer brugen af stored procedures i transaktioner, at koden bliver nemmere at vedligeholde?
[[Stored Procedures]] forenkler transaktionshåndtering ved at modulere logikken.

##### Hvilke fordele giver brugen af output-parametre i stored procedures, når du arbejder med transaktioner?
Output-parametre i stored procedures giver øjeblikkelig feedback, nyttig i beslutningstagning under transaktioner.

---

## Øvelse 3: Triggers til dataintegritet og forretningsregler

**_Forventning_**: Bruge triggers til at sikre dataintegritet og håndhæve forretningsregler.

Opret en trigger kaldet trg_CheckStockBeforeInsert, der udløses, når en ny post indsættes i ORDERITEM-tabellen. [[Triggers|Triggeren]] skal kontrollere, om der er nok lagerbeholdning af det valgte produkt i PRODUCT-tabellen. Hvis der ikke er nok lager, skal triggeren forhindre indsættelsen og vise en fejlmeddelelse.  
  
```SQL
CREATE TRIGGER trg_CheckStockBeforeInsert
ON ORDERITEM
FOR INSERT
AS
BEGIN
    DECLARE @PRODUCTID INT, @QUANTITY INT, @CURRENTSTOCK INT;
    
    SELECT @PRODUCTID = ProductID, @QUANTITY = Quantity FROM inserted;
    SELECT @CURRENTSTOCK = StockQuantity FROM PRODUCT WHERE ProductID = @productID;
    
    IF @QUANTITY > @CURRENTSTOCK
    BEGIN
        RAISERROR ('Insufficient stock', 16, 1);
        ROLLBACK;
    END
END;
```

---

## Øvelse 4: Oprettelse af triggers til automatiske handlinger
**_Forventning_**: Lære at oprette triggers, der udfører automatiske handlinger baseret på dataændringer.

---

#### Øvelse 4.1:

Opret en trigger på ORDERITEM-tabellen, der udløses AFTER INSERT. Triggeren skal opdatere PRODUCT-tabellen og reducere lagerbeholdningen, men kun hvis produktet er valgt til kurven (SelectedToCart = 1).
```SQL
CREATE TRIGGER trg_UpdateProductStockAfterInsert
ON ORDERITEM
AFTER INSERT
AS
BEGIN
	UPDATE PRODUCT 
	SET StockQuantity = StockQuantity - inserted.Quantity
	FROM inserted
	WHERE inserted.ProductID = PRODUCT.ProductID AND inserted.SelectedToCart = 1
END;
```

Test triggeren ved at køre en INSERT statement på ORDERITEM-tabellen og SELECT statement på PRODUCT-tabellen.

---

#### Øvelse 4.2:
Opret en trigger på SHOPPINGCART-tabellen, der udløses AFTER INSERT. Triggeren skal reducere kundens point i CUSTOMER-tabellen baseret på den brugte points, hvis nogle er brugt.
```SQL
CREATE TRIGGER trg_UpdateCustomerPointsAfterInsert
ON Orders
AFTER INSERT
AS
BEGIN
    UPDATE Customers
    SET points = points - inserted.used_points
    FROM inserted
    WHERE Customers.customer_id = inserted.customer_id;
END;
```

Test triggeren ved at køre en INSERT statement på SHOPPINGCART-tabellen og SELECT statement på CUSTOMER-tabellen.

---

#### Øvelse 4.3:
Opret en trigger på Payment-tabellen, der udløses AFTER INSERT. Triggeren skal opdatere OrderStatus i SHOPPINGCART-tabellen til ’Paid’.
```SQL
CREATE TRIGGER trg_UpdateOrderStatusToPaidOnPaymentInsert
ON Payment
AFTER INSERT
AS
BEGIN
    DECLARE @orderID INT;

    SELECT @orderID = order_id
    FROM inserted;

    UPDATE SHOPPINGCART
    SET order_status = 'Paid'
    WHERE order_id = @orderID;
END;
```

Test triggeren ved at køre en INSERT statement på Payment-tabellen og SELECT statement på SHOPPINGCART-tabellen.

---

#### Øvelse 4.4:
Opret en trigger på SHIPMENT-tabellen, der udløses AFTER INSERT. Triggeren skal opdatere OrderStatus i SHOPPINGCART-tabellen til Shipped.
```SQL
CREATE TRIGGER trg_UpdateOrderStatusToShippedOnShipmentInsert
ON SHIPMENT
AFTER INSERT
AS
BEGIN
    DECLARE @orderID INT;

    SELECT @orderID = order_id
    FROM inserted;

    UPDATE SHOPPINGCART
    SET order_status = 'Shipped'
    WHERE order_id = @orderID;
END;
```

Test triggeren ved at køre en INSERT statement på SHIPMENT-tabellen og SELECT statement på SHOPPINGCART-tabellen.

---

#### Øvelse 4.5:
Opret en trigger på SHOPPINGCART-tabellen, der udløses AFTER UPDATE, når status ændres til "Paid". Triggeren skal opdatere kundens point i CUSTOMER-tabellen baseret på den samlede værdi af de valgte produkter i kurven.
```SQL
CREATE TRIGGER trg_UpdateCustomerPointsOnOrderPaid
ON SHOPPINGCART
AFTER UPDATE
AS
BEGIN
    IF UPDATE(order_status)
    BEGIN
        DECLARE @customerID INT, @totalPrice FLOAT;

        SELECT @customerID = customer_id, @totalPrice = sum_price
        FROM inserted
        WHERE order_status = 'Paid';

        UPDATE Customer
        SET points = points + (@totalPrice / 10)
        WHERE customer_id = @customerID;
    END
END;
```

Test triggeren ved at køre en UPDATE statement på SHOPPINGCART-tabellen og SELECT statement på CUSTOMER-tabellen.


---

## Øvelse 5: Triggers til Logning
**_Forventning_**: Skab logningstriggers for at holde styr på ændringer i kritiske tabeller.

Opret en trigger kaldet trg_LogShoppingCartChanges på SHOPPINGCART-tabellen, der udføres AFTER INSERT eller AFTER UPDATE. Triggeren skal logge alle ændringer i en separat logtabel, SHOPPINGCART_LOG. Logtabellen skal indeholde følgende felter:
- OrderID: Ordrenummeret for den aktuelle ændring.
- CustomerID: Kundens ID for den aktuelle kurv.
- OrderStatusID: Status-ID for ordren (fx "Paid", "Shipped" osv.).
- TotalPrice: Den samlede pris på ordren.
- ProductCount: Antal produkter (linjevarer) i ordren.
- LogDate: Den aktuelle dato og tidspunkt, hvor ændringen sker.
- LoggedUser: Navnet på den bruger, der udførte ændringen.

```SQL
CREATE TRIGGER trg_LogShoppingCartChanges
ON SHOPPINGCART
AFTER INSERT, UPDATE
AS
BEGIN
    INSERT INTO SHOPPINGCART_LOG (OrderID, CustomerID, OrderStatusID, TotalPrice, ProductCount, LogDate, LoggedUser)
    SELECT 
        order_id, 
        customer_id, 
        order_status, 
        sum_price, 
        (SELECT COUNT(*) FROM Product_Orders WHERE Product_Orders.order_id = inserted.order_id), 
        GETDATE(), 
        SUSER_SNAME()
    FROM inserted;
END;
```

---

# Øvelse 6: Vidensdeling kl. 14:30

**_Forventning_**: Til slut kan du diskutere følgende spørgsmål med dine kolleger for at sikre forståelsen af, hvad I har arbejdet med:

##### Hvorfor er ACID-principperne (Atomicity, Consistency, Isolation, Durability) vigtige for transaktioner i databaser?
- **Atomicity**: Garanterer, at en transaktion enten gennemføres fuldstændigt eller slet ikke. Hvis en fejl opstår under en transaktion, kan den annulleres, så ingen halvfærdige data bliver gemt. Det sikrer, at deloperationer inden for en transaktion ikke påvirker data inkonsistent.

- **Consistency**: Sikrer, at en transaktion bringer databasen fra én konsistent tilstand til en anden. Regler og begrænsninger på data (såsom primærnøgler og referentiel integritet) håndhæves, så data altid forbliver konsistente.

- **Isolation**: Sikrer, at transaktioner køres uafhængigt af hinanden. Dette betyder, at en transaktions midlertidige ændringer ikke bliver synlige for andre transaktioner, før den er afsluttet, hvilket forhindrer datakonflikter og race conditions.

- **Durability**: Garanterer, at når en transaktion er bekræftet (committed), bliver dens ændringer permanent gemt, selv ved systemnedbrud. Dette sikres gennem lagring af data på disk og brug af sikkerhedskopier.
##### Hvordan kan brugen af ROLLBACK i en transaktion håndtere fejl og forbedre datareliabilitet?
[[ROLLBACK]] i en transaktion tillader databasen at fortryde alle ændringer, der er udført i løbet af en transaktion, hvis en fejl opstår. 
Hvis en transaktion eksempelvis mislykkes på grund af en lagerbeholdning, som går i minus, vil en **ROLLBACK** sikre, at ingen af transaktionens ændringer gemmes. 
Dette forbedrer datareliabiliteten, da vi undgår delvise opdateringer, som kunne føre til en inkonsistent database. 
Ved at kunne fortryde ændringer skabes en sikkerhedsmekanisme, som hjælper med at sikre, at dataene kun gemmes, hvis alle dele af transaktionen er gennemført korrekt.
##### Hvilke situationer er ideelle for brug af triggers frem for stored procedures?
Triggers er ideelle, når handlinger skal udløses automatisk som reaktion på ændringer i data. Typiske situationer inkluderer:

1. **Automatisering af Dataintegritet**: Triggers kan bruges til automatisk at kontrollere forretningsregler, som at sikre, at en produktmængde ikke går i minus ved nye ordrer.
2. **Sporing og Logning**: Triggers er gode til logning af ændringer i vigtige tabeller, fx at registrere hver gang der sker en ændring i en kundes ordrehistorik.
3. **Kaskaderende Opdateringer**: Når en ændring i én tabel skal påvirke relaterede tabeller, kan triggers bruges til at sikre, at alle nødvendige opdateringer sker samtidig.

Stored procedures, på den anden side, bruges ofte mere fleksibelt til at køre bestemte opgaver efter behov og kan kaldes eksplicit af applikationen, mens triggers er bundet til specifikke databaseevents.
##### Hvilken værdi tilfører logningstriggers som trg_LogShoppingCartChanges, når det gælder revision og sporing af ændringer?

Logningstriggers som `trg_LogShoppingCartChanges` skaber en revisionsspor, der kan være værdifuld for både fejlfinding og compliance.

- **Revisionsspor**: Logning af ændringer giver et detaljeret spor af, hvem der har foretaget ændringer, hvornår de blev foretaget, og hvilke data der blev ændret. Dette er nyttigt, hvis det senere bliver nødvendigt at forstå tidligere ændringer eller analysere systemaktivitet.
- **Sporing af Brugere og Ændringer**: Da logningstriggeren gemmer navnet på den bruger, der udførte ændringen, gør den det nemmere at identificere, hvilke brugere der har foretaget bestemte opdateringer.
- **Compliance og Sikkerhed**: Mange industrier kræver bevis på datahistorik for at overholde regulatoriske krav. Logningstriggeren sikrer, at alle ændringer er dokumenteret uden afhængighed af manuelle logs, hvilket kan hjælpe med at efterleve sådanne krav.

Logningstriggeren øger på den måde gennemsigtigheden og pålideligheden af data i systemet.