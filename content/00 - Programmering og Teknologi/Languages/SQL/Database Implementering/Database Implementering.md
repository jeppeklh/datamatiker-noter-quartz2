tags: #Programmering #SQL

> [!tldr] Definition
> Den anden fase omfatter følgende fem implementeringstrin illustreret i figur forneden:
> ![[Database Implementeringstrin.png]]

Disse trin tager udgangspunkt i en UML-databasemodel for domænet designet i fase A og resulterer i en kørende database-instans i et R-DBMS, som realiserer databasemodellen:

1. Brug af SQL Data Definition Language (SQL DDL) som specifikation af database og dens indhold
    
2. Definition af SQL-databasen via SQL DDL
    
3. Definition af alle tabeller (relationer) i databasemodellen via SQL DDL
    
4. Definition af primær- og fremmednøgler (constraints) via SQL DDL
    
5. Kørsel af alle SQL DDL definitioner fra foregående trin i MS SQL Server med en resulterende kørende database til følge (fasens slutprodukt)


_Ved afslutningen af Fase B vil du have en fuldt funktionel database, der er designet og implementeret i overensstemmelse med de bedste praksis inden for databaseudvikling. Dette danner grundlaget for videre arbejde med datahåndtering, forespørgsler og optimering i efterfølgende faser._

---

## Trin 1 - Brug af SQL DDL som specifikation
I denne fase er der udelukkende fokus på den del af SQL, nærmere betegnet SQL DDL, som berører oprettelse mm. af en database samt oprettelse mm. af tabeller.

---

## Trin 2 -Definition af SQL-databasen via SQL DDL
For at oprette en database, benytter man SQL DDL kommandoen:
```SQL
CREATE DATABASE database-name;
```
Hvis man har oprettet adskillige databaser i MS SQL Server, kan man skifte mellem dem med kommandoen:
```SQL
USE database-name;
```

Man kan omslutte databasenavnet (og stort set alle navne) med kantede parenteser. Det kan være en fordel, hvis man anvender mellemrum i navnet (hvilket ikke anbefales).

---

## Trin 3 - Definition af tabeller (relationer) via SQL DDL
Nu er det tid til at tage fat i UML-[[Databasemodel|databasemodellen]] og definere de [[Table|tabeller]], som [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|databasen]] skal indeholde. Til dette arbejde indeholder databasemodellen alle nødvendige informationer med navngivning af tabeller, kolonner og deres datatyper, nøgler samt restriktioner.

Vi kigger på modellen fra eksemplet i [[Database Design]]
![[Databasemodel eksempel 4.png]]
Oprettelse af SEMESTER-tabellen (uden i første omgang at tage hensyn til nøgler):
```SQL
CREATE TABLE SEMESTER (
  SemesterId Int,
  Number Int
);
```

Den næste tabel er PARTICIPANT-tabellen:
```SQL
CREATE TABLE PARTICIPANT (
  Email NVarChar(50),
  FirstName NVarChar(30),
  LastName NVarChar(40),
  ImagePath NVarChar(100),
  SemesterId Int
);
```
Gennemgår man nu hele UML-databasemodellen får man følgende samlet definition for alle 7 tabeller i databasen:
```SQL
CREATE TABLE SEMESTER (
  SemesterId Int,
  Number Int
);

CREATE TABLE PARTICIPANT (
  Email NVarChar(50),
  FirstName NVarChar(30),
  LastName NVarChar(40),
  ImagePath NVarChar(100),
  SemesterId Int
);

CREATE TABLE SUBJECT (
  SubjectId Int,
  Title NVarChar(30),
  SemesterId Int
);

CREATE TABLE TEACHER (
  Email Int,
  SubjectId Int
);

CREATE TABLE STUDENT (
  Email Int,
  Badge NVarChar(30)
);

CREATE TABLE LESSON (
  LessonId Int,
  Date DateTime2,
  SubjectId Int
);

CREATE TABLE PARTICIPANT_LESSON (
  Email Int,
  LessonId Int
);
```

Hvis ovenstående blev eksekveret i et R-DBMS, så ville disse tabeller blive tilsvarende oprettet i nævnte rækkefølge. Bemærk at tabeller for oven i princippet kan defineres i en vilkårlig rækkefølge.

---

## Definition af primær- og fremmednøgler via SQL DDL
Når sammenhængen mellem tabellerne defineres via nøgler, så er rækkefølgen, som [[Table|tabeller]] defineres i, særdeles vigtigt. Hvis en tabel refererer til en anden tabel via en [[FOREIGN KEY|fremmednøgle]], så skal den refererede tabel være defineret før den refererende tabel. 
Dvs. man starter først med at definere de tabeller, der er uafhængige af andre tabeller.

---

#### Primærmøgler
En [[PRIMARY KEY|primærnøgle]] defineres via en tilsvarende [[Restriktion|restriktion]] i SQL. En restriktion kan angives enten unavngiven eller med navn.

```SQL
CREATE TABLE SEMESTER (
  SemesterId Int PRIMARY KEY,
  Number Int NOT NULL
);
```

Her er der angivet en unavngivet restriktion ’PRIMARY KEY’ ud for SemesterId-kolonnen, da den skal fungere som en primærnøgle. 
Samtidig er der angivet en ’NOT NULL’-restriktion ud for Number-kolonnen for at sikre, at tilsvarende celler i tabellen altid skal have en værdi angivet. 
En kolonne, der er en primærnøgle, skal have en værdi, så her behøver man ikke at angive ’NOT NULL’.

Hvis man vælger en navngiven restriktion for primærnøglen:
```SQL
CREATE TABLE SEMESTER (
  SemesterId Int,
  Number Int NOT NULL,
  CONSTRAINT PK_Semester PRIMARY KEY (SemesterId)
)
```
Her defineres en restriktion med navnet ’PK_Semester’, som angiver, at SemesterId-kolonnen skal være tabellens primærnøgle. 
Hvis en primærnøgle består af mere end én kolonne, så skal man anvende en navngiven restriktion.

Fortsætter vi med at definere primærnøgler for alle tabeller (samt ’NOT NULL’-restriktioner) fås:
```SQL
CREATE TABLE SEMESTER (
  SemesterId Int PRIMARY KEY,
  Number Int NOT NULL
);

CREATE TABLE PARTICIPANT (
  Email NVarChar(50) PRIMARY KEY,
  FirstName NVarChar(30) NOT NULL,
  LastName NVarChar(40) NOT NULL,
  ImagePath NVarChar(100) NOT NULL,
  SemesterId Int NOT NULL
);

CREATE TABLE SUBJECT (
  SubjectId Int PRIMARY KEY,
  Title NVarChar(30) NOT NULL,
  SemesterId Int NOT NULL
);

CREATE TABLE TEACHER (
  Email Int PRIMARY KEY,
  SubjectId Int NOT NULL
);

CREATE TABLE STUDENT (
  Email Int PRIMARY KEY,
  Badge NVarChar(30) NOT NULL
);

CREATE TABLE LESSON (
  LessonId Int PRIMARY KEY,
  Date DateTime2 NOT NULL,
  SubjectId Int NOT NULL
);

CREATE TABLE PARTICIPANT_LESSON (
  Email Int,
  LessonId Int,
  CONSTRAINT PK_ParticipantLesson PRIMARY KEY (Email, LessonId)
);
```

---

#### Fremmenøgler
Man skal i definitionen af [[FOREIGN KEY|fremmednøglen]] skal referere til den refererede [[Table|tabel]] med navn,så rækkefølgen tabel-definationer bliver vigtig.

Den første tabel med en fremmednøgle, som kun er afhængig af SEMESTER-tabellen, er PARTICIPANT-tabellen.
Her er SemesterId-kolonnen en fremmednøgle til SEMESTER-tabellen. 
Denne restriktion kan efterfølgende defineres unavngivet med SQL-kommandoen:
```SQL
CREATE TABLE PARTICIPANT (
  Email NVarChar(50) PRIMARY KEY,
  FirstName NVarChar(30) NOT NULL,
  LastName NVarChar(40) NOT NULL,
  ImagePath NVarChar(100) NOT NULL,
  SemesterId Int NOT NULL FOREIGN KEY REFERENCES SEMESTER(SemesterId)
);
```
Med ’FOREIGN KEY’ angives typen af restriktionen og med ’REFERENCES’ angives hvilken tabel og hvilke kolonner, der refereres til.
Bemærk i øvrigt, at ’NOT NULL’-restriktionen er bevaret for SemesterId-kolonnen, da en fremmednøgle faktisk godt kan have en null-værdi.

 Restriktionen for fremmednøglen kan navngives med følgende:
```SQL
 CREATE TABLE PARTICIPANT (
  Email NVarChar(50) PRIMARY KEY,
  FirstName NVarChar(30) NOT NULL,
  LastName NVarChar(40) NOT NULL,
  ImagePath NVarChar(100) NOT NULL,
  SemesterId Int NOT NULL,
  CONSTRAINT FK_Participant_Semester FOREIGN KEY (SemesterId) 
                                     REFERENCES SEMESTER(SemesterId)
);
```
Den navngivne restriktion for fremmednøglen skal (som det også gælder for primærnøglen) anvendes, hvis der indgår mere end én kolonne i nøglen, eller hvis fremmednøglen også allerede er en primærnøgle.

Fortsætter vi med at definere fremmednøgler for alle tabeller fås nu:
```SQL
CREATE TABLE SEMESTER (
  SemesterId Int PRIMARY KEY,
  Number Int NOT NULL
);

CREATE TABLE PARTICIPANT (
  Email NVarChar(50) PRIMARY KEY,
  FirstName NVarChar(30) NOT NULL,
  LastName NVarChar(40) NOT NULL,
  ImagePath NVarChar(100) NOT NULL,
  SemesterId Int NOT NULL FOREIGN KEY REFERENCES SEMESTER(SemesterId)
);

CREATE TABLE SUBJECT (
  SubjectId Int PRIMARY KEY,
  Title NVarChar(30) NOT NULL,
  SemesterId Int NOT NULL FOREIGN KEY REFERENCES SEMESTER(SemesterId)
);

CREATE TABLE TEACHER (
  Email NVarChar(50) PRIMARY KEY,
  SubjectId Int NOT NULL FOREIGN KEY REFERENCES SUBJECT(SubjectId),
  CONSTRAINT FK_Teacher_Participant FOREIGN KEY (Email) 
                                    REFERENCES PARTICIPANT(Email)
);

CREATE TABLE STUDENT (
  Email NVarChar(50) PRIMARY KEY,
  Badge NVarChar(30) NOT NULL,
  CONSTRAINT FK_Student_Participant FOREIGN KEY (Email) 
                                    REFERENCES PARTICIPANT(Email)
);

CREATE TABLE LESSON (
  LessonId Int PRIMARY KEY,
  Date DateTime2 NOT NULL,
  SubjectId Int NOT NULL FOREIGN KEY REFERENCES SUBJECT(SubjectId)
);

CREATE TABLE PARTICIPANT_LESSON (
  Email NVarChar(50),
  LessonId Int,
  CONSTRAINT PK_ParticipantLesson PRIMARY KEY (Email, LessonId),
  CONSTRAINT FK_ParticipantLesson_Participant FOREIGN KEY (Email) 
                                              REFERENCES PARTICIPANT(Email),
  CONSTRAINT FK_ParticipantLesson_Lesson FOREIGN KEY (LessonId) 
                                         REFERENCES LESSON(LessonId)
);
```

---

## Trin 5 - Kørsel af alle SQL DDL definitioner til oprettelse af kørende SQL-database
Ovennævnte fælles definition af database, tabeller og nøgle kan kopieres over i et nyt ’Query’-vindue i værktøjet ’Microsoft SQL Server Management Studio’ og derfra afvikles via Execute-kommando (markeret øverst med rødt) og resultatet af kørslen er oprettelsen af de 7 tabeller, som også er indikeret med rødt i ’Object Explorer’ til venstre.
![[Pasted image 20240903221203.png]]
**Husk at tage backup:**   
Når I arbejder med database implementering, er det afgørende at sikre, at jeres arbejde ikke går tabt. For at beskytte jeres arbejde og gøre det lettere at gendanne i tilfælde af fejl eller tab af data, bør I altid tage en kopi af jeres database definitioner, tabeller og nøgle kommandoer.   
**Sådan gør I:**

1. Kopiér jeres SQL-kode: Når I definerer en database, opretter tabeller eller udfører andre vigtige SQL-operationer, skal I kopiere koden og gemme den i en tekstfil.
2. Navngiv og organisér filerne: Giv filerne meningsfulde navne (f.eks. database_definition.txt, table_creation_commands.sql) og opret en struktur, der gør det nemt at finde de nødvendige filer senere.
3. Gem filerne et sikkert sted: Gem jeres backup-filer et sikkert sted, så I har adgang til dem, selvom noget går galt med jeres primære lagringsenhed.

---

## Related Topics
- Link
- 

---

## Resources
- [Fase B Læringsobjekt (DDL)](https://scorm.itslearning.com/data/3289/C20150/ims_import_9/scormcontent/index.html#/lessons/DhdYeDLCjTxYebTC4TyKq2ozXtycvdcd)
- 