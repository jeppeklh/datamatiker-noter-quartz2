tags: #Programmering #SQL

## Definition 
---
En essentiel del af [[Databaseadminstration]], der sikrer, at kun autoriserede personer har adgang til systemets data og funktioner.

SQL Server tilbyder en robust mekanisme til at oprette og administrere brugere, definere roller og tildeling af tilladelser for at beskytte data mod uautoriseret adgang og manipulation.
## Roller og tilladelser i SQL Server
---
SQL Server burgre roller til at gruppere brugerr med lignende adgangsbehov.

Der findes 2 typer af roller:

#### Serverroller
---
Disse roller kan hjælpe dig med at organisere og begrænse adgang til SQL Server, så kun autoriserede brugere kan udføre bestemte administrative opgaver.
###### sysadmin 
Har fuld kontrol over SQL Server-instansen. Kan udføre enhver opgave og har adgang til alle serverressourcer.
###### serveradmin 
Kan konfigurere serverniveau-indstillinger, såsom ændring af serveregenskaber og stoppe/start af serveren.
###### setupadmin
Kan administrere linked servers og udføre administrative opgaver relateret til opsætning af serveren.
###### securityadmin
Ansvarlig for sikkerhed. Kan administrere logins og tilladelser på serverniveau. Kan også ændre adgangskoder for logins.
###### processadmin
Kan afslutte kørende processer på serveren, såsom hængende eller langvarige forespørgsler.
###### diskadmin
Administrerer diskfilerne i SQL Server. Bruges primært til opgaver relateret til administration af databasefiler.
###### dbcreator
Kan oprette, ændre og slette databaser på SQL Server. Har ikke rettigheder til at administrere serverindstillinger eller sikkerhed.
###### bulkadmin
Kan udføre bulk data-indlæsninger ved hjælp af BULK INSERT-kommandoen.
#### Database-specifikke roller
---
Disse roller gør det nemt at styre og tildele rettigheder til brugere på databaseniveau, afhængig af deres funktioner og ansvarsområder.

###### db_owner
Har fuld kontrol over den specifikke database. Kan udføre enhver handling inden for databasen, herunder ændring af struktur og sikkerhed.
###### db_securityadmin
Kan administrere sikkerhedsrelaterede indstillinger i databasen, såsom brugerrettigheder og roller. 
###### db_accessadmin
Kan tilføje eller fjerne adgangen til databasen for logins.    
###### db_backupoperator
Kan tage backups af databasen.
###### db_ddladmin
Kan udføre enhver DDL (Data Definition Language) kommando, såsom oprettelse eller ændring af objekter i databasen (tabeller, indekser, visninger, etc.).
###### db_datawriter
Har tilladelse til at indsætte, opdatere og slette data i alle brugerdefinerede tabeller i databasen.    
###### db_datareader
Har tilladelse til at læse data fra alle tabeller og visninger i databasen.    
###### db_denydatawriter
Blokerer for, at brugeren kan indsætte, opdatere eller slette data i databasen.    
###### db_denydatareader
Blokerer for, at brugeren kan læse data fra tabeller i databasen.


## Oprettelse af en bruger
---
Med queries:
[[Uge44 - Databaseadministration og sikkerhed#Opret brugere og tilknyt dem til roller|Opret login, brugere og roller opgaver]]
#### Trin 1: Opret et login
---
Login er den server-niveau-adgang, som giver brugeren adgang til SQL Server-instansen.

1. Åbn **SQL Server Management Studio (SSMS)**, og forbind til din SQL Server-instans.
    
2. I Object Explorer, udvid **Security**, højreklik på **Logins**, og vælg **New Login**.
    
3. I dialogboksen **Login – New**, udfyld følgende:
    
    - **Login Name**: Indtast brugerens navn.
        
    - **Authentication**:
        
        - Vælg **SQL Server Authentication**, og angiv en adgangskode, hvis du vil oprette en SQL Server-login.
            
        - Vælg **Windows Authentication**, hvis du vil bruge et eksisterende Windows-brugerlogin.
            
    - Hvis det er SQL Server Authentication, kan du også markere **Enforce password policy**, hvis du ønsker at håndhæve adgangskodepolitikker.
        
4. Under **Default Database**, vælg den database, som skal være brugerens standarddatabase.
    
5. Klik på **OK** for at oprette login.

#### Trin 2: Opret en databasebruger
---
En databasebruger er nødvendig for at give adgang til en bestemt database.

1. I Object Explorer, udvid den **ønskede** database, udvid **Security**, højreklik på **Users**, og vælg **New User**.
    
2. I dialogboksen **Database User – New**, udfyld følgende:
    
    - **User name**: Indtast brugerens navn.
        
    - **Login name**: Klik på **Search** og vælg det login, du oprettede i Trin 1.
        
    - **Default schema**: Vælg eventuelt et standard schema (_f.eks. dbo_).
        
3. Under **Role Membership**, vælg de roller, som denne bruger skal være medlem af (_f.eks. db_datareader, db_datawriter_).
    
4. Klik på **OK** for at oprette brugeren.
#### Trin 3: Tildel tilladelser (hvis nødvendigt)
---
Med queries:
[[Uge44 - Databaseadministration og sikkerhed#Trin 2 Tildel rettigheder til Views og Stored Procedures|Tildel rettigheder opgaver]]

Hvis du ønsker at give specifikke tilladelser, kan du gøre det enten ved hjælp af roller (_som i Trin 2_) eller ved at tildele direkte tilladelser til brugeren.

1. I Object Explorer, udvid databasen, og højreklik på et objekt, f.eks. en tabel.
    
2. Vælg **Properties**, og klik på fanen **Permissions**.
    
3. Vælg den bruger, du lige har oprettet, og tildel de ønskede tilladelser (f.eks. **SELECT**, **INSERT**, **UPDATE**, **DELETE**).
    
4. Klik på **OK**.
#### Trin 4: Test adgang
---
For at sikre, at brugeren har de korrekte rettigheder, kan du logge ud af SQL Server og logge ind igen med de nyoprettede brugeroplysninger. 
Test, at brugeren kan tilgå de nødvendige databaser og udføre de nødvendige operationer.




## Related Topics
---
- [[Databaseadminstration]]
- [[Backup og Gendannelse af Data]]

## Resources
---
- [Databaseadministration og sikkerhed Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_22/scormcontent/index.html#/lessons/j0JwBgonhudyZjizr36yeaxYlUIs0GBQ)
