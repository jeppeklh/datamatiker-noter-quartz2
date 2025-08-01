tags: #Programmering #SQL

## Definition 
---
Sikkerhed er en afgørende del af enhver databaseadministration, da den beskytter data mod uautoriseret adgang, manipulation og tab. 

SQL Server tilbyder en række indbyggede mekanismer til at sikre både adgangsstyring og datakryptering, så følsomme data kan beskyttes både i transit og ved lagring.
## Brugergodkendelse og Autorisation
---
#### 1. Windows-godkendelse

- Integreres med Windows Active Directory, hvilket gør det muligt at bruge eksisterende Windows-login for brugergodkendelse.
    
- Anvender **Kerberos**-protokollen til sikker adgangskontrol, hvilket sikrer central styring af brugerrettigheder.
    

#### 2. SQL Server-godkendelse

- SQL Server Authentication kræver et separat login og adgangskode, som kun bruges i SQL Server.
    
- Det er nyttigt i miljøer uden Active Directory-integration eller ved adgang fra eksterne applikationer.
### Eksempel på oprettelse af SQL Server login og tildeling af rolle
---
```SQL
-- Opret SQL Server-login
CREATE LOGIN BrugerLogin WITH PASSWORD = 'SikkerAdgang123';

-- Opret en bruger i databasen og tildel rolle
USE [Databasenavn];
CREATE USER BrugerLogin FOR LOGIN BrugerLogin;
EXEC sp_addrolemember 'db_datareader', 'BrugerLogin';
```



## Datakryptering (TDE, Always Encrypted)
---
Datakryptering beskytter data mod uautoriseret adgang ved at gøre dem ulæselige for uautoriserede brugere. SQL Server tilbyder flere metoder til at sikre kryptering af data.

#### 1. Transparent Data Encryption (TDE)

- **TDE** krypterer hele databasen, herunder backupfiler, hvilket sikrer, at dataene er krypterede i ro (på disk).
    
- Det er "transparent" for applikationer, da krypteringen sker automatisk, uden at applikationen behøver at ændres.

##### Eksempel på aktivering af TDE
```SQL
-- Opret en krypteringsnøgle
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'SikkerNøgle123';

-- Opret en databasekrypteringsnøgle
CREATE CERTIFICATE TDECert WITH SUBJECT = 'TDE Certifikat';
USE [Databasenavn];
CREATE DATABASE ENCRYPTION KEY
WITH ALGORITHM = AES_256
ENCRYPTION BY SERVER CERTIFICATE TDECert;

-- Aktivér TDE
ALTER DATABASE [Databasenavn] SET ENCRYPTION ON;
```

#### 2. Always Encrypted

- **Always Encrypted** er designet til at beskytte følsomme data (som personnumre og kreditkortnumre) ved at kryptere dem både i transit og ved lagring. Krypteringen udføres på klientsiden, hvilket betyder, at SQL Server aldrig ser de ukrypterede data.
    
- Nøglerne, der bruges til kryptering, gemmes uden for SQL Server, ofte i en sikker nøglelager (som Azure Key Vault), hvilket yderligere øger sikkerheden
##### Eksempel på brug af Always Encrypted
```SQL
-- Krypter en kolonne i en tabel ved hjælp af Always Encrypted
CREATE COLUMN MASTER KEY MyCMK
WITH KEY_STORE_PROVIDER_NAME = 'MSSQL_CERTIFICATE_STORE',
KEY_PATH = 'CurrentUser/My/Certificatetest';

CREATE COLUMN ENCRYPTION KEY MyCEK
WITH COLUMN_MASTER_KEY = MyCMK,
ALGORITHM = 'RSA_OAEP';

CREATE TABLE FølsomData
(
    ID INT PRIMARY KEY,
    FølsomKolonne NVARCHAR(100) COLLATE Latin1_General_BIN2
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = MyCEK, ENCRYPTION_TYPE = Randomized)
);
```
## Related Topics
---
- [[Uge44 - Databaseadministration og sikkerhed|Databaseadministation og sikkerhed Opgaver]]
- 

## Resources
---
- Link
- 