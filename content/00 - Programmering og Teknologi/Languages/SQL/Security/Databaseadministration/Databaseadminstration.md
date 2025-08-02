tags: #Programmering #SQL

> [!tldr] Definition
> En databaseadminstrator (DBA) sikrer at en organisations databaser fungerer optimalt.
> Ansvarlig for installation, konfiguration, opdatering, vedligeholdelse og overvågning af databasesystemet.

Arbejder tæt sammen med udviklere og systemadminstratorer.
Beskytter data mod tab, uautoriseret adgang og data korruption gennem backup, gendannelse og sikkerhedsforanstaltninger.

Har også en vigtig rolle i cloud-administation såsom Microsoft Azure.

---

## SQL Server Arkitektur
SQL Server arkitekturen er bygget op af flere lag. 
De vigtigste elementer i arkitekturen er:

##### Relational Engine
Denne del håndterer SQL-forespørgsler, indeksering, datavalidering og udførelse af transaktioner. Det er hjertet i SQL Server, hvor forespørgsler analyseres, optimeres og udføres.

##### Storage Engine 
Denne komponent er ansvarlig for fysisk lagring af data på disk, organisering af sider og filer samt administration af transaktionslogge og bufferpool. 

##### SQL OS (Operating System)
SQL Server fungerer ovenpå et dedikeret operativsystem-lag kaldet SQL OS, som håndterer lav-niveau opgaver som planlægning, I/O management og hukommelsesstyring.

##### Buffer Manager
Dette subsystem optimerer ydelsen ved at cache data i hukommelsen, så forespørgsler ikke altid kræver diskadgang.

![[SQL Server Arkitektur.png]]

---

### SQL Server-komponenter
SQL Server består af flere nøglekomponenter, som tilsammen understøtter databasens drift og funktioner

##### Database Engine
Denne komponent styrer lagring, forespørgselshåndtering og transaktionsstyring. Det er her, dataene gemmes og forespørges fra.

##### SQL Server Agent
Bruges til at automatisere opgaver som backup, vedligeholdelse og jobs, der kan køre planlagt.

##### SQL Server Integration Services (SSIS)
Et værktøj til dataintegration og ETL (Extract, Transform, Load), der bruges til at flytte data mellem forskellige systemer.

##### SQL Server Reporting Services (SSRS)
Til rapportgenerering og distribution, hvilket gør det muligt at oprette og dele rapporter baseret på data fra SQL Server.

##### SQL Server Analysis Services (SSAS)
Bruges til datamining og analyse af store mængder data, ofte i OLAP-kuber til hurtige forespørgsler.

---

## Related Topics
- [[Brugeradministration og Roller]]
- [[Backup og Gendannelse af Data]]
- [[Høj Tilgængelighed og Disaster Recovery]]
- [[Uge44 - Databaseadministration og sikkerhed|Databaseadministation og sikkerhed Opgaver]]

---

## Resources
- Link
- 