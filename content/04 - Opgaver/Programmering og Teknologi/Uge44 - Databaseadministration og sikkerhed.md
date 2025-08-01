Database administration og sikkerhed I dag kommer du til at arbejde med brugeradministration i webshop-databasen. Øvelserne vil fokusere på at oprette og administrere brugere, logins og roller, samt håndtere rettigheder for at sikre, at adgangen til databasen er korrekt kontrolleret og sikret. Du vil også lære at implementere backup-strategier og kryptering af data for at beskytte følsomme oplysninger som kunde- og ordredata. Til sidst bliver der inkluderet en praktisk øvelse i at anvende TDE (Transparent Data Encryption) for at sikre, at dine data er krypterede i databasen.

## Øvelse 1: Terminologi
---
Forventning: At få en klar forståelse af de grundlæggende begreber inden for brugeradministration og datasikkerhed samt GDPR-overholdelse.

Brug "Ordet rundt" til at reflektere over begreberne:

##### 1. Hvordan kan brugere og roller hjælpe med at beskytte data i en database? Overvej her principperne for least privilege (mindste privilegium) for at sikre, at hver bruger kun har adgang til de data og funktioner, der er nødvendige for deres rolle
---
Brug af _roller_ og _brugere_ er essentiel for at begrænse adgang via _least privilege_ princippet, hvilket betyder, at hver bruger kun får adgang til de data og funktioner, de absolut behøver.
Dette mindsker risikoen for uautoriseret adgang og reducerer potentielle sikkerhedstrusler.

##### 2. Hvad er en passende rollefordeling i en webshop-database (fx admin, lagerpersonale, kundeservice)?
---
- **Admin**: fuld adgang til systemet og dataadministration.
- **Kundeservice**: læseadgang til kunde- og ordredata, begrænset redigeringsret.
- **Lagerpersonale**: læseadgang til produkt- og lagerdata, begrænset opdateringsret på lagerbeholdning.

##### 3. Hvorfor er backup af databasen vigtig for en webshop? Hvad kan der ske, hvis en webshop mister data fra kunder eller ordrer?
---
Backup er vitalt for at undgå permanent datatab. 
En webshop uden backup risikerer tab af kunde- og ordredata, hvilket kan skade både kundetillid og virksomhedens drift.
##### 4. Diskutér logning og audit trails som en del af GDPR-overholdelse: Hvordan kan disse hjælpe med at sikre og overvåge adgang til følsomme data i databasen
---
Audit trails hjælper med at overvåge og dokumentere adgang til følsomme data, hvilket er et krav i GDPR-overholdelse. 
Logning gør det muligt at spore, hvem der har adgang til hvilke data og hvornår.


## Øvelse 2: Oprettelse af login, brugere og roller
---
Forventning: At oprette brugere og roller til webshoppersonale og tildele rettigheder, der sikrer, at adgang til data er kontrolleret og beskyttet.

Udfør følgende på Microsoft SQL Server Management Studio:

##### Trin 1: Opret brugere og roller
---
###### Opret roller for forskellige funktioner i webshoppen:
---
Vi opretter roller til forskellige medarbejdere i webshoppen, såsom kundeservice og lagerpersonale, baseret på tidligere oprettede views og stored procedures fra sidste uge.
```SQL
CREATE ROLE KundeserviceRole;
CREATE ROLE LagerRole;
```

###### Opret brugere og tilknyt dem til roller
---
Opret logins og tilknyt brugere til rollerne. Disse brugere vil få tildelt adgang til de relevante views og stored procedures.
```SQL
-- Opret login
CREATE LOGIN KundeserviceUser WITH PASSWORD = 'SecurePassword123';
CREATE LOGIN LagerUser WITH PASSWORD = 'SecurePassword456';

-- Opret brugere i databasen og tilknyt til roller
CREATE USER KundeserviceUser FOR LOGIN KundeserviceUser;
CREATE USER LagerUser FOR LOGIN LagerUser;

ALTER ROLE KundeserviceRole ADD MEMBER KundeserviceUser;
ALTER ROLE LagerRole ADD MEMBER LagerUser;

```
##### Trin 2: Tildel rettigheder til Views og Stored Procedures
---
Vi vil nu tildele adgang til de allerede oprettede views og stored procedures, som du tidligere har arbejdet med, i stedet for at skrive nye.

###### Tildel rettigheder til KundeserviceRole
---
Kundeservice kan have adgang til views og stored procedures, der involverer kunde- og ordredata.

Giv SELECT-rettigheder til relevante views, som du allerede har oprettet til kundeservice, f.eks. vwOrderCustomer
```SQL
GRANT SELECT ON vwOrderCustomer TO KundeserviceRole;
```

 Giv EXECUTE-rettigheder til eksisterende stored procedures, der tillader opdatering af kundeoplysninger (uspUpdateCustomerPoints).
```SQL
GRANT EXECUTE ON uspUpdateCustomerPoints TO KundeserviceRole;
```

###### Tildel rettigheder til LagerRole
---
Lagerpersonalet skal have adgang til produkt- og lagerdata, men kun via de relevante views og stored procedures, som du allerede har oprettet.

 Giv SELECT-rettigheder til eksisterende views, der viser produkt- og lagerinformation (vwLowStockProducts).
```SQL
GRANT SELECT ON vwLowStockProducts TO LagerRole;
```

Giv EXECUTE-rettigheder til stored procedures, der tillader opdatering af lagermængder (opret proceduren hvis du ikke har oprettet den).
```SQL
GRANT EXECUTE ON uspUpdateStock TO LagerRole;
```

#### Trin 3: Test adgang og rettigheder
---
Test nu rollerne ved at logge ind som forskellige brugere og afprøve deres rettigheder. Vær særlig opmærksom på at sikre least privilege i praksis ved at begrænse adgangen til kun de nødvendige data og funktioner.Test som KundeserviceUser

 Log ind som KundeserviceUser og kør en SELECT på det eksisterende view, som viser kunde- og ordreoplysninger: 
```SQL
 SELECT * FROM vwOrderCustomer;
```

Prøv at opdatere en kundes points ved hjælp af den eksisterende stored procedure (uspUpdateCustomerPoints).

Test som LagerUser

Log ind som LagerUser og kør en SELECT på det eksisterende view, som viser produkt- og lageroplysninger (vwLowStockProducts).

Prøv at opdatere en produktslagermængde ved hjælp af den stored procedure du har oprettet for denne formål.

Prøv at få adgang til kunde- og ordredata, og bemærk, at adgangen nægtes, og diskuter betydningen af least privilege.



## Øvelse 3: Backup og gendannelse af databasen
---
Forventning: At forstå og udføre backup og gendannelse af databasen samt diskutere en effektiv backup-strategi for en webshop.

Udfør følgende på Microsoft SQL Server Management Studio:

##### 1. Tag en fuld backup af WebshopDB.
```SQL
BACKUP DATABASE WebshopDB TO DISK = 'C:\backups\WebshopDB_full.bak';
```
##### 2. Tag en differentiel backup efter nogle ordrer er registreret.
```SQL
BACKUP DATABASE WebshopDB TO DISK = 'C:\backups\WebshopDB_diff.bak' WITH DIFFERENTIAL;
```

##### 3. Test gendannelse af databasen fra backup.
Luk først alle forbindelser.
```SQL
ALTER DATABASE WebshopDB SET SINGLE_USER WITH ROLLBACK IMMEDIATE;
```

```SQL
RESTORE DATABASE WebshopDB FROM DISK = 'C:\backups\WebshopDB_full.bak' WITH NORECOVERY;
RESTORE DATABASE WebshopDB FROM DISK = 'C:\backups\WebshopDB_diff.bak' WITH RECOVERY;
```

##### 4. Diskutér, hvordan en god backup-strategi kunne se ud for en webshop, og hvor ofte man bør tage fulde, differentielle og log-backups.

## Øvelse 4: Implementering af Transparent Data Encryption (TDE)
---
Forventning: At sikre følsomme oplysninger i webshop-databasen ved at anvende TDE.

##### 1. Hvad er Transparent Data Encryption (TDE)? 
**Transparent Data Encryption (TDE)** beskytter data ved at kryptere dem på disk.
En master key bruges til at beskytte krypteringsnøglerne.
###### **1. Hvordan sikrer det, at følsomme oplysninger såsom kundeoplysninger og betalingsdata er beskyttet mod uautoriseret adgang?** 
TDE sikrer følsomme oplysninger som kunde- og betalingsdata mod uautoriseret fysisk adgang til disken, fx hvis filerne kopieres fra serveren.
###### **2. Diskutér også krypteringsnøglernes håndtering, og hvorfor korrekt opbevaring af krypteringsnøgler er afgørende for datasikkerheden. Hvad ville konsekvenserne være, hvis en krypteringsnøgle mistes.**
**Krypteringsnøgler** spiller en central rolle i TDE. Databasen opretter en _database-krypteringsnøgle_ (Database Encryption Key - DEK), som beskyttes af et certifikat, der igen beskyttes af en _master key_. Hvis nøglerne ikke opbevares korrekt, kan data tabes permanent, fordi de krypterede data ikke kan dekrypteres uden de oprindelige nøgler

##### 2. Opret en master key til at beskytte krypteringsnøglerne.
```SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'StrongMasterKeyPassword!';
```
##### 3. Opret et certifikat til krypteringsnøglen.
```SQL
CREATE CERTIFICATE TDECert WITH SUBJECT = 'TDE Encryption Certificate';
```
##### 4. Opret en krypteringsnøgle til databasen og aktiver TDE.
```SQL
CREATE DATABASE ENCRYPTION KEY WITH ALGORITHM = AES_256 ENCRYPTION BY SERVER CERTIFICATE TDECert;
ALTER DATABASE WebshopDB SET ENCRYPTION ON;
```
##### 5. Verificér krypteringsstatus: SELECT name, is_encrypted
```SQL
SELECT name, is_encrypted 
FROM sys.databases 
WHERE name = 'WebshopDB';
```

## Øvelse 5: Vidensdeling kl. 14:30
---
Forventning: At evaluere, hvad du har lært om brugeradministration, backup-strategier og kryptering af data.

· Hvordan sikrer roller i webshop-databasen, at ingen medarbejdere får for mange rettigheder? Diskutér princippet om least privilege.

· Hvilke udfordringer kan der være ved backup og gendannelse af data i travle webshops?

· Hvilke fordele og udfordringer er der ved at bruge views og stored procedures i forbindelse med brugerrettigheder?

· Hvordan kan kryptering (TDE) beskytte webshoppen mod brud på persondatasikkerheden?

· Hvordan kan logning af adgang til følsomme data og audit trails hjælpe med at sikre overholdelse af GDPR og andre lovkrav?

Tidsramme: 30 minutter