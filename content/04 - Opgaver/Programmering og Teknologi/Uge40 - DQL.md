#opgaver #Programmering 

Du har allerede arbejdet grundigt med database-design i Fase A, hvor du udviklede en UML-database model og normaliserede dine data. I Fase B omsatte du dette design til en fungerende database ved at oprette tabeller gennem SQL's Data Definition Language (DDL) og manipulere data med Data Manipulation Language (DML). Nu er tiden kommet til at forespørge databasen ved hjælp af Data Query Language (DQL). I dette opgavesæt vil du gennemgå, hvordan du kan hente og analysere data fra din database via SELECT-sætningen, filtrere resultater med WHERE, kombinere data fra flere tabeller med JOINs, og anvende aggregeringsfunktioner til at bearbejde og fortolke dine data. Dette vil give dig den nødvendige viden og færdigheder til effektivt at udtrække relevant information fra Webshop databasen.

# Øvelse 1: Terminologi
---
**_Forventning_:** At sikre, at du har en klar forståelse af de grundlæggende begreber inden for DQL, som er nødvendige for at arbejde med at udtrække relevant information fra databasen.

Brug **Ordet rundt** til at reflektere over begreberne:

##### **Forklar begrebet DQL. Hvordan adskiller DQL sig fra andre SQL-sprog såsom DDL og DML?**

DQL er en del af SQL, der bruges til at forespørge (spørge) og hente data fra en database. Det adskiller sig fra [[DDL Overview|DDL]] (Data Definition Language), som bruges til at definere og ændre databaser (oprette tabeller, ændre kolonner osv.), og fra [[DML Overview|DML]] (Data Manipulation Language), der bruges til at indsætte, opdatere eller slette [[Data|data]] i [[Table|tabeller]].

##### **Hvad er en forespørgsel (en: Query), og hvordan bruges den i DQL til at hente data fra en relationel database?**

En SQL-forespørgsel er en kommando, der henter data fra en relationel database. Med DQL bruges forespørgsler via [[SELECT]]-sætningen til at hente specifikke data ud fra givne kriterier.

##### **Hvad er general syntaks af et SELECT-statement?**

```SQL
SELECT column1, column2
FROM table_name
WHERE condition;
```

##### **Forklar forskellen mellem en SQL-betingelse (en: SQL Clause) som WHERE og HAVING.**

[[WHERE Clause|WHERE]] bruges til at filtrere rækker, før en gruppering finder sted. Den anvendes direkte på data i tabellen.

[[HAVING]] bruges til at filtrere resultater efter en gruppering ([[GROUP BY]]), typisk med aggregeringsfunktioner (som [[SUM()]], [[COUNT()]] osv.).

##### **Hvad er en JOIN i SQL? Beskriv kort formålet med en JOIN og forklar de forskellige typer af JOINs, herunder INNER JOIN, LEFT JOIN, RIGHT JOIN og FULL JOIN.**

En [[Joins|JOIN]] bruges til at kombinere rækker fra to eller flere tabeller baseret på en fælles kolonne.

[[Inner Join|INNER JOIN]]: Returnerer kun de rækker, hvor der er et match i begge [[Table|tabeller]].

[[Left Join|LEFT JOIN]]: Returnerer alle rækker fra den venstre tabel, og de tilsvarende rækker fra den højre tabel. Hvis der ikke er noget match, vil ``NULL`` blive returneret for den højre tabel.

[[Right Join|RIGHT JOIN]]: Returnerer alle rækker fra den højre tabel og de tilsvarende rækker fra den venstre tabel.

[[Full Join|FULL JOIN]]: Returnerer alle rækker, hvor der er et match i enten venstre eller højre tabel.

##### **Hvad er aggregeringsfunktioner i SQL? Forklar formålet med disse funktioner.**

Disse er funktioner, der tager flere værdier og returnerer en enkelt værdi, såsom:

[[COUNT()]]: Antallet af rækker.

[[SUM()]]: Summen af værdier.

[[AVG()]]: Gennemsnittet af værdier.

[[MIN() and MAX()#MAX() eksempel|MAX()]]: Den højeste værdi.

[[MIN() and MAX()#MIN() eksempel|MIN()]] Den laveste værdi.

Sørg for at alle får mulighed for at tale.

_Tidsramme: 30 minutter_

# Øvelse 2: Simple SELECT Statements
---
**_Forventning_**: At få praktisk erfaring med at hente data fra databaser ved hjælp af simple [[SELECT]]-sætning.

Udfør følgende på Microsoft SQL Server Management Studio:

**Skriv en forespørgsel, der henter alle oplysninger om alle kunder fra CUSTOMER-tabellen.**

```SQL
SELECT * 
FROM CUSTOMER;
```

**Hent kun kundenavn, email og points fra CUSTOMER-tabellen.**

```SQL
SELECT CustomerID, Email, Points 
FROM CUSTOMER;
```

**Hent en liste over alle unikke byer, hvor kunder bor. ([[SELECT DISTINCT Statement|DISTINCT]])**

```SQL
SELECT DISTINCT City
FROM CUSTOMER;
```

**Hent alle produkter, der hører til Category 1.**

```SQL
SELECT *
FROM PRODUCT
WHERE CategoryID = 1;
```


**Hent alle kundeoplysninger og sorter dem alfabetisk efter kundenavn i stigende rækkefølge.**

```SQL
SELECT *
FROM CUSTOMER
ORDER BY FirstName ASC;
```


**Hent CustomerName, city og points, og sorter dem efter antal optjente point i faldende rækkefølge.**

```SQL
SELECT FirstName,LastName,City,Points 
FROM CUSTOMER 
ORDER BY Points DESC;
```

**Hent alle oplysninger om kunder, der bor i København.**

```SQL
SELECT *  
FROM CUSTOMER  
WHERE City = 'København';
```

**Hent alle kunder, der har optjent flere end 300 point.
**
```SQL
SELECT *  
FROM CUSTOMER  
WHERE Points > 300;
```

**Hent 10 dyreste produkter. (TOP)**

```SQL
SELECT TOP 10 * 
FROM PRODUCT 
ORDER BY Price DESC;
```

**Hent alle ordre, der ikke er leveret.**

```SQL
SELECT * 
FROM SHOPPINGCART JOIN ORDERSTATUS 
ON SHOPPINGCART.OrderStatusID = ORDERSTATUS.OrderStatusID 
WHERE ORDERSTATUS.OrderStatusName != 'Delivered'; 
```
  
_Tidsramme: 30 minutter_

# Øvelse 3: Operatører
----
**_Forventning_**: At anvende logiske og sammenligningsoperatører til at filtrere og manipulere data.

Udfør følgende på Microsoft SQL Server Management Studio:

**Find alle kunder, der bor i København og har optjent mere end 100 point.**

```SQL
SELECT *
FROM CUSTOMER
WHERE City = 'København' 
AND Points > 100;
```

**Find alle produkter, der har mindre end 5 stk. på lager.**

```SQL
SELECT *
FROM PRODUCT
WHERE StockQuantity < 5;
```

**Find alle kunder, der bor enten i København eller Aarhus.**

```SQL
SELECT *
FROM CUSTOMER
WHERE City = 'København'
OR City =  'Aarhus';
```

**Find alle kunder, der ikke bor i Odense.**

```SQL
SELECT *
FROM CUSTOMER
WHERE City != 'Odense';
```

**Find alle produkter, der har "Telefon" i navnet. ([[LIKE Operator|LIKE]])**

```SQL
SELECT *
FROM PRODUCT
WHERE ProductName LIKE '%Telefon%';
```

**Find alle kunder, der bor i byer, der slutter med ”borg”. ([[Wildcards]])**

```SQL
SELECT *
FROM CUSTOMER
WHERE City LIKE '%borg';
```

**Find alle kunder, der bor i en af følgende byer: København, Aarhus, eller Odense. ([[IN Operator|IN]])**

```SQL
SELECT *
FROM CUSTOMER
WHERE City IN ('København', 'Aarhus', 'Odense');
```

**Find alle produkter, der koster mellem 100 og 500 kr. ([[BETWEEN Operator|BETWEEN]])**

```SQL
SELECT *
FROM PRODUCT
WHERE Price BETWEEN 100 AND 500;
```

**Find alle ordre mellem 01-01-2024 og 31-08-2024. ([[BETWEEN Operator|BETWEEN]])**

```SQL
SELECT *
FROM SHOPPINGCART
WHERE OrderDate BETWEEN '2024-01-01' AND '2024-08-31';
```

**Vis kundens navn og tilføj en kolonne, der viser "GOLD" hvis kunden har optjent over 500 point, ”SILVER” hvis kunden har optjent mellem 301 og 500 ellers vis "BRONZE". (Kan løses enten med [[CASE Expression|CASE]] eller [[UNION Operator|UNION]] – Benyt gerne [[SQL Aliases|Alias]] ved den nye kolonne)**

```SQL
SELECT FirstName, LastName
       CASE
          WHEN Points > 500 THEN 'GOLD'
          WHEN Points BETWEEN 301 AND 500 THEN 'SILVER'
          ELSE 'BRONZE'
   END AS MembershipLevel
FROM CUSTOMER;
```


_Tidsramme: 30 minutter_

# Øvelse 4: Aggregeringsfunktioner
---
**_Forventning_**: At få en praktisk forståelse af aggregeringsfunktioner i SQL og deres anvendelse.

Udfør følgende på Microsoft SQL Server Management Studio:

Find den laveste og højeste pris på alle produkter.

```SQL
SELECT MIN(Price) AS LowestPrice,
       MAX(Price) AS HighestPrice
FROM PRODUCT;
```

**Find det samlede antal kunder i databasen.**

```SQL
SELECT COUNT(*) AS TotalCustomers
FROM CUSTOMER;
```

**Find det samlede beløb af alle ordrer i databasen.**

```SQL
Select SUM(Quantity * Price) AS SumOfAllOrders 
FROM ORDERITEM;
```

**Find den gennemsnitlige pris på alle produkter.**

```SQL
Select AVG(Price) AS AverageProductPrice 
FROM PRODUCT;
```

**Find antal produkter for hver produktkategori.**

```SQL
SELECT CategoryName, COUNT(*) AS ProductCount
FROM PRODUCT
GROUP BY CategoryName;
```

**Find antal stk. i alt for hver ordre.**

```SQL
SELECT OrderID, SUM(Quantity) AS Quantity
FROM ORDERITEM
GROUP BY OrderID;
```

**Find alle produktkategorier, hvor den gennemsnitlige produktpris er over 2300 kr.**

```SQL
SELECT CategoryID, AVG(Price) AS AveragePrice 
FROM PRODUCT 
GROUP BY CategoryID 
HAVING AVG(Price) > 2300
```

**Find antallet af ordrer for hver kunde, og vis kun kunder, der har afgivet mere end 5 ordrer.**

```SQL
SELECT CUSTOMER.CustomerID, FirstName, LastName
FROM CUSTOMER INNER JOIN SHOPPINGCART 
ON CUSTOMER.CustomerID = SHOPPINGCART.CustomerID 
GROUP BY Customer.CustomerID, CUSTOMER.FirstName, CUSTOMER.LastName 
HAVING COUNT(SHOPPINGCART.CustomerID) > 2
```
  
_Tidsramme: 45 minutter_

# Øvelse 5: JOINS
---
**_Forventning_**: At få en praktisk erfaring med at bruge forskellige typer af JOIN-sætninger i SQL for at kombinere data fra flere tabeller.

Udfør følgende på Microsoft SQL Server Management Studio:

**Find og vis CustomerName, OrderID, OrderDate, PointsUsed og OrderStatus for alle ordre.**

```SQL
SELECT CONCAT(CUSTOMER.FirstName, ' ', CUSTOMER.LastName) AS CustomerName,
	   SHOPPINGCART.OrderID, 
	   SHOPPINGCART.OrderDate, 
	   SHOPPINGCART.PointsUsed, 
	   ORDERSTATUS.OrderStatusName
FROM SHOPPINGCART JOIN CUSTOMER
ON SHOPPINGCART.CustomerID = CUSTOMER.CustomerID
JOIN ORDERSTATUS
ON ORDERSTATUS.OrderStatusID = SHOPPINGCART.OrderStatusID;
```

**Find og vis CustomerName, OrderID, OrderDate og PaymentMethod for alle ordre, der er mere end 5 år gammel.**

```SQL
SELECT CONCAT(CUSTOMER.FirstName, ' ', CUSTOMER.LastName) AS CustomerName,
	   SHOPPINGCART.OrderID, 
	   SHOPPINGCART.OrderDate, 
	   PAYMENTMETHOD.PaymentMethodName
FROM SHOPPINGCART JOIN CUSTOMER
ON SHOPPINGCART.CustomerID = CUSTOMER.CustomerID
JOIN PAYMENTMETHOD
ON SHOPPINGCART.PaymentMethodID = PAYMENTMETHOD.PaymentMethodID
WHERE YEAR(SHOPPINGCART.OrderDate) <= 2019;
```


**Find og vis CustomerName, Country, OrderID, OrderDate, og TotalPrice for kunder, der har foretaget ordrer med en totalbeløb over 2000 kr.**

```SQL
SELECT CONCAT(FirstName, ' ', Lastname) AS CustomerName,
	   Country, 
	   ORDERITEM.OrderID,
	   SHOPPINGCART.OrderDate,
	   SUM(ORDERITEM.Price * ORDERITEMQuantity) AS TotalPrice
FROM SHOPPINGCART JOIN CUSTOMER
ON SHOPPINGCART.CustomerID = CUSTOMER.CustomerID
JOIN ORDERITEM
ON SHOPPINGCART.OrderID = ORDERITEM.OrderID)
GROUP BY SHOPPINGCART.OrderID, 
	     LastName, 
	     FirstName, 
	     Country,  
	     SHOPPINGCART.OrderDate
HAVING SUM(ORDERITEM.Price*ORDERITEM.Quantity) > 2000;
```

**Find alle produkter i købskurven for en kunde med et givet CustomerName. Vis ProductName, Quantity, og Price for hvert produkt i kundens kurv.**

```SQL
SELECT FirstName, 
	   LastName, 
	   ProductName, 
	   Quantity, 
	   PRODUCT.Price 
FROM CUSTOMER JOIN SHOPPINGCART 
ON CUSTOMER.CustomerID = SHOPPINGCART.CustomerID 
JOIN ORDERITEM 
ON SHOPPINGCART.OrderID = ORDERITEM.OrderID 
JOIN PRODUCT ON 
ORDERITEM.ProductID = PRODUCT.ProductID 
WHERE FirstName = 'John' AND LastName = 'Doe';

```

**Find alle kunder og vis deres ordrer, hvis nogen. Inkluder kunder uden ordrer. Vis CustomerName,  Country, OrderID, og OrderDate. ([[Left Join|LEFT JOIN]])**

```SQL
SELECT CUSTOMER.FirstName, 
	   CUSTOMER.LastName, 
	   CUSTOMER.Country, 
	   SHOPPINGCART.OrderID, 
	   SHOPPINGCART.OrderDate 
FROM CUSTOMER LEFT JOIN SHOPPINGCART 
ON CUSTOMER.CustomerID = SHOPPINGCART.CustomerID 
ORDER BY OrderID;
```

 **Find alle produkter, uanset om de er blevet solgt. Vis ProductID, ProductName og OrderID. ([[Right Join|RIGHT JOIN]])**

```SQL
SELECT PRODUCT.ProductID, 
	   PRODUCT.ProductName, 
	   ORDERITEM.OrderID 
FROM PRODUCT LEFT JOIN ORDERITEM 
ON PRODUCT.ProductID = PRODUCT.ProductID;
```

**Find alle kunder, der bor i samme land, og vis deres navne parvist. ([[Self Join|SELF JOIN]])** 

```SQL
SELECT CONCAT(c1.FirstName, ' ', c1.LastName) AS Customer1Name,
	   CONCAT(c2.FirstName, ' ', c2.LastName) AS Customer2Name, 
	   c1.Country 
FROM CUSTOMER c1 JOIN CUSTOMER c2 
ON c1.Country = c2.Country AND c1.CustomerID < c2.CustomerID 
ORDER BY c1.Country, c1.CustomerID, c2.CustomerID;
```

**Vis OrderID, OrderDate, CustomerName, ProductID, ProductName, Price, Quantity og SubTotal for alle ordre. ([[Inner Join|JOIN]] 4 tabeller)**

```SQL
SELECT ORDERITEM.OrderID, 
	   SHOPPINGCART.OrderDate, 
	   CONCAT(FirstName, ' ', LastName) AS CustomerName, 
	   PRODUCT.ProductID, 
	   PRODUCT.ProductName, 
	   PRODUCT.Price, 
	   ORDERITEM.Quantity, 
       (PRODUCT.Price * ORDERITEM.Quantity) AS SubTotal 
FROM CUSTOMER 
JOIN SHOPPINGCART ON CUSTOMER.CustomerID = SHOPPINGCART.CustomerID 
JOIN ORDERITEM ON SHOPPINGCART.OrderID = ORDERITEM.OrderID 
JOIN PRODUCT ON ORDERITEM.ProductID = PRODUCT.ProductID;
```

_Tidsramme: 60 minutter_

# Øvelse 6: Vidensdeling kl. 14:30
---
I dag har vi arbejdet med at opbygge en dybere forståelse af SQL's Data Query Language (DQL), med særlig fokus på SELECT-sætningen, aggregeringsfunktioner og forskellige JOIN-typer. Vi har udforsket, hvordan DQL kan anvendes til at hente og analysere data fra en relationel database på en effektiv måde. Gennem praktiske øvelser har vi lært at filtrere, sortere og kombinere data fra flere tabeller.  
  
Ved at anvende SQL-sætninger, har vi også set, hvordan komplekse forespørgsler kan konstrueres for at løse forretningsspørgsmål som visning af kundeoplysninger, salgshistorik og produktoversigter.

**Fremvisning**

I slutningen af lektionen bør du være i stand til at: (Vis et eksempel på hvert punkt)

·        Udtrække specifikke data fra en database ved hjælp af SELECT-sætningen.

·        Anvende filtre og betingelser gennem WHERE, AND, OR, og andre operatorer.

·        Sammenfatte data ved hjælp af aggregeringsfunktioner som COUNT(), SUM(), AVG(), og anvende GROUP BY og HAVING til at analysere grupperede resultater.

·        Bruge INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN og SELF JOIN til at kombinere data fra flere tabeller og håndtere relationer mellem forskellige datasæt.

_Tidsramme: **30** minutter_