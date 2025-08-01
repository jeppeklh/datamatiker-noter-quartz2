tags: #Programmering #SQL

## Definition 
---
**Høj tilgængelighed og disaster recovery** (_HA/DR_) refererer til metoder og teknologier, der anvendes til at sikre, at en database er tilgængelig, selv under hardwarefejl, softwarefejl eller katastrofer.
## Always On Availability Groups
---
Availability Groups muliggør failover af flere databaser som en enhed og tillader samtidig adgang til read-only kopier af [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|databasen]] (_sekundære replikaer_) for at forbedre ydeevnen og tilgængeligheden.

#### Nøglefunktioner:

- **Høj tilgængelighed**: Op til 8 sekundære replikaer kan synkroniseres med primæren, hvoraf 2 kan være synkroniserede og klar til automatisk failover.
    
- **Read-only sekundære replikaer**: Læs-forespørgsler kan dirigeres til sekundære replikaer, hvilket aflaster primæren og forbedrer ydelsen.
    
- **Disaster Recovery**: Data synkroniseres mellem primær og sekundær replika i realtid, hvilket sikrer minimal datatab i tilfælde af et nedbrud.
#### Eksempel på SQL kommando
---
```SQL
CREATE AVAILABILITY GROUP [AG1]
FOR DATABASE [Databasenavn]
REPLICA ON 'PrimaryServer' WITH
(
    ENDPOINT_URL = 'TCP://PrimaryServer:5022',
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
    FAILOVER_MODE = AUTOMATIC
),
'SecondaryServer' WITH
(
    ENDPOINT_URL = 'TCP://SecondaryServer:5022',
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
    FAILOVER_MODE = AUTOMATIC
);
```


## Failover Clustering
---
**Failover Clustering** er en metode, der gør det muligt for SQL Server at køre på en cluster af servere (_noder_), hvor en instans af SQL Server kan flyttes fra én node til en anden i tilfælde af fejl, hvilket sikrer høj tilgængelighed.

#### Nøglefunktioner:

- **Fælles lager**: Alle noder i clusteret deler det samme lager, hvilket sikrer, at data er tilgængelige uanset hvilken node, der kører instansen.
    
- **Automatisk failover**: Hvis den aktive node fejler, overføres SQL Server-tjenesten automatisk til en anden node.
    
- **Geografisk failover**: Med stretch clustering kan failover finde sted på tværs af geografiske lokationer for disaster recovery-scenarier.

## Replikation og Log Shipping
---
### Replikation
---
**Replikation** er en metode til at distribuere og synkronisere data fra én database til andre ved hjælp af publish-subscribe modellen. Replikation kan anvendes til høj tilgængelighed, lastfordeling, eller for at give adgang til data fra forskellige geografiske placeringer.

SQL Server understøtter forskellige typer replikation:
- **Snapshot Replication**: Kopierer og distribuerer data ved faste intervaller.
- **Transactional Replication**: Synkroniserer løbende transaktioner fra publikation til abonnenter.
- **Merge Replication**: Tillader, at data kan ændres på både publikation og abonnent, hvorefter ændringerne flettes sammen.

#### Eksempel på SQL kode for at oprette replication:
```SQL
EXEC sp_replicationdboption 
    @dbname = N'Databasenavn', 
    @optname = N'publish', 
    @value = N'true';

EXEC sp_addpublication 
    @publication = N'DatabasePublication', 
    @dbname = N'Databasenavn', 
    @status = N'active';

EXEC sp_addarticle 
    @publication = N'DatabasePublication', 
    @article = N'Tabelnavn', 
    @source_table = N'Tabelnavn';
```
### Log Shipping
---
**Log Shipping** er en enkel, men effektiv metode til disaster recovery, hvor transaktionslogfiler fra en primær database kontinuerligt sendes til en eller flere sekundære servere. Disse logfiler bruges til at holde sekundære servere opdaterede med ændringer fra den primære database. Log Shipping muliggør manuel failover, hvis den primære server fejler.

#### Nøglefunktioner:

- **Tidsplanlagt backup**: Transaktionslogfiler fra primær database tages på faste tidspunkter og kopieres til en sekundær server.
    
- **Automatisk gendannelse**: Sekundære servere gendanner transaktionslogfiler og opdaterer databasen.
    
- **Disaster recovery**: I tilfælde af nedbrud på den primære server kan en administrator manuelt gøre en sekundær server til den nye primære server.

#### Eksempel på SQL-kommandoer:
---
```SQL
-- Backup loggen på primær server
BACKUP LOG [Databasenavn]
TO DISK = 'C:\Backup\Databasenavn_Log.bak';

-- Restore loggen på sekundær server
RESTORE LOG [Databasenavn]
FROM DISK = 'C:\Backup\Databasenavn_Log.bak'
WITH NORECOVERY;
```
## Related Topics
---
- Link
- 

## Resources
---
- Link
- 