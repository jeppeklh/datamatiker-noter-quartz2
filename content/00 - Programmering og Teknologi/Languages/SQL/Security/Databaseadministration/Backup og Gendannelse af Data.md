tags: #Programmering #SQL

## Definition 
---
I SQL Server er backup og gendannelse af data centrale elementer i databaseadministration, der sikrer dataintegritet og tilgængelighed. 
SQL Server understøtter forskellige typer backup, og der er flere strategier, som kan implementeres for at opnå maksimal beskyttelse af data.
## Forskellige typer backup
---
SQL Server understøtter tre primære typer af backup, hver med sin egen funktion og anvendelse

#### Full Backup
---
Indeholder en komplet kopi af alle data i databsen på tidspunktet for backuppen.
Den mest grundlæggende tupe af backup og udgør grundlaget for de andre backuptyper.
```SQL
BACKUP DATABASE [Databasenavn] 
TO DISK = 'C:\Backup\Databasenavn_Full.bak';
```
#### Differential Backup
---
Gemmer kin de data, der er ændret siden den seneste [[#Full Backup]].
Dette reducerer størrelsen og tiden for backuppen.
For at gendanne fra en differential backup kræves både den sidste Full Backup og den seneste differential backup,
```SQL
BACKUP DATABASE [Databasenavn]
TO DISK = 'C:\Backup\Databasenavn_Diff.bak'
WITH DIFFERENTIAL;
```
#### Transaction Log Backup
---
En Transaction Log Backup gemmer alle transaktioner, der er sket siden den sidste Trnasaction Log Backup.
Dette gør det muligt at gendanne databasen til ethvert tidspunkt ved hjælp af transaction loggen.
Bruges ofte i scenarier, hvor kontinuerlig databeskyttelse er kritisk.

```SQL
BACKUP LOG [Databasenavn]
TO DISK = 'C:\Backup\Databasenavn_Log.bak';
```
### Gengannelsesmodeller og strategier
---
SQL Server tilbyder tre gendannelsesmodeller, der styrer, hvordan transaktionslogge håndteres, og dermed hvordan data kan gendannes:

#### Simple Recovery Model
---
I denne model slettes transaktionslogge automatisk efter hver checkpoint, hvilket minimerer behovet for log management. Dette er velegnet til mindre kritiske databaser, hvor der ikke er behov for avanceret gendannelse.

###### Eksempel
Bruges typisk til databaser, hvor man kun tager full og differential backups, og hvor man ikke behøver at gendanne til et specifikt tidspunkt.

#### Full Recovery Model
---
Denne model giver mulighed for at gendanne data til et hvilket som helst tidspunkt, da alle transaktioner gemmes i transaktionsloggen, indtil de er sikkerhedskopieret. Dette er den mest sikre model og anbefales til mission-kritiske databaser.

###### Eksempel
Bruges, når både full backups, differential backups og transaction log backups anvendes. Det muliggør fuld genoprettelse af data, inklusive point-in-time gendannelse.

#### Bulk-Logged Recovery Model
---
Denne model minder om Full Recovery, men minimerer logningen af bulk-operationer som store INSERT eller SELECT INTO operationer. Det er nyttigt, når der skal håndteres store datamængder med minimal logforbrug, men det begrænser mulighederne for point-in-time gendannelse.

###### Eksempel
Bruges, når store mængder data skal flyttes hurtigt, og point-in-time gendannelse ikke er kritisk på det tidspunkt.


## Backup Strategier
---
Når du udarbejder en backup-strategi, bør du tage følgende overvejelser i betragtning:

- **Full Backup Strategi**: Udfør regelmæssige full backups, f.eks. ugentligt, og kombiner dette med differential eller transaction log backups for at sikre hyppig databeskyttelse.
    
- **Differential Backup Strategi**: Tag daglige differential backups efter en full backup for at reducere størrelsen og tiden for backuppen, men stadig give mulighed for hurtig gendannelse.
    
- **Transaction Log Backup Strategi**: Tag transaction log backups flere gange om dagen, afhængigt af hvor meget data der ændres, for at sikre minimal datatab og muligheden for at gendanne til et bestemt tidspunkt.

En veludviklet backup- og gendannelsesstrategi kombinerer disse teknikker for at sikre optimal databeskyttelse med minimal nedetid i tilfælde af fejl.

### Indbyggede muligheder for backup i SQL Server
---
SQL Server tilbyder flere indbyggede værktøjer og funktioner til at oprette backups af dine databaser uden at skulle anvende tredjepartssoftware. 
Disse værktøjer giver fleksibilitet i både planlægning og udførelse af backup-opgaver:

1. **SQL Server Management Studio (SSMS)**
    
    - Her har du mulighed for gennem et brugervenligt interface at vælge den type backup, du vil tage (full, differential, transaction log), samt specificere lagringsplacering og planlægge automatiserede backups.
        
    - **Sådan bruges det**:
        1. Højreklik på databasen i Object Explorer.
        2. Vælg **Tasks** > **Back Up**.
        3. Vælg backup-type (Full, Differential, Transaction Log).
        4. Vælg backup-destination (disk, tape, etc.).
        5. Klik på **OK** for at udføre backuppen eller planlæg en job til senere.
            
2. **Transact-SQL (T-SQL)**
    
    - SQL giver mulighed for at automatisere backups ved at skrive scripts. Dette er en fleksibel måde at administrere backups på, da du kan planlægge, eksekvere og tilpasse backups præcis efter dine behov.
        
    - **Eksempel på script
```SQL
    BACKUP DATABASE [Databasenavn]
TO DISK = 'C:\Backup\Databasenavn_Full.bak'
WITH INIT;
```
3. **SQL Server Agent**
    
    1. **SQL Server Agent** er et jobplanlægningsværktøj, der gør det muligt at automatisere backups. Du kan oprette jobs, der udfører backups på faste tidspunkter (f.eks. dagligt, ugentligt) og sende notifikationer ved succes eller fejl.
        

	 - **Sådan bruges det**:
	    1. I SSMS, gå til Object Explorer og udvid SQL Server Agent.
	    2. Opret et nyt job under **Jobs**.
	    3. Tilføj et nyt trin, hvor du indtaster et T-SQL backup script.
	    4. Planlæg jobben til at køre automatisk på bestemte tidspunkter.
        
4. **Maintenance Plans**
    
    - **Maintenance Plans** i SQL Server gør det nemt at oprette backups ved hjælp af en grafisk grænseflade, der ikke kræver, at du skriver T-SQL-kode. Du kan oprette planlagte opgaver for at udføre regelmæssige backups og andre vedligeholdelsesopgaver som indeksering og databaseoprydning.
        
    - **Sådan bruges det**:
        1. I SSMS, gå til Object Explorer og udvid **Management**.
        2. Højreklik på **Maintenance Plans** og vælg **New Maintenance Plan**.
        3. Brug værktøjet til at oprette en backup-plan ved at vælge backup-tasken og konfigurere tidspunkter og backup-indstillinger.
            
5. **Azure Backup til SQL Server (til cloud-databaser)**
    
    - Hvis du kører SQL Server på Azure, kan du bruge **Azure Backup** til at tage automatiserede og skalerbare backups af dine databaser. Dette er en cloud-baseret løsning, der integrerer med SQL Server og understøtter både full, differential og transaction log backups.
        
    - **Sådan bruges det**: 
	    Opsætning sker gennem Azure-portalen, hvor du kan definere backup-politikker og vælge, hvor ofte backups skal foretages.
## Related Topics
---
- [[Databaseadminstration]]
- [[Høj Tilgængelighed og Disaster Recovery]]

## Resources
---
- [Databaseadministation og sikkerhed Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_22/scormcontent/index.html#/lessons/BzkYKXmpmbQ5KI5SIjczZLsQ8RF0hWM9)
- 