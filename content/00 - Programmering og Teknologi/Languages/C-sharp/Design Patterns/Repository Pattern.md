---
aliases:
  - repository-mønster
---
tags: #C-sharp #Programmering #DesignPattern #RepositoryPattern

## Definition 
---
Repository-mønstret er et designmønster, der giver en abstraktion over datalaget i en applikation. 

Det giver en samling af [[Methods Overview|metoder]] til at manipulere [[Data|data]], hvilket gør det lettere at skifte datakilder eller udføre [[MSTest|enhedstest]]. 

Repositories hjælper med at reducere afhængigheder mellem forretningslogik og dataadgangslogik.

Det giver en ren tilgang til databaseoperationer såsom Create, Read, Update og Delete ([[CRUD Operations|CRUD]]).

Uanset om du udvikler en konsolapplikation, en WPF-applikation eller en webbaseret løsning, vil måden, du interagerer med [[Data|data]], være den samme, så længe du følger **Repository Pattern**.
## Fordele
---
Repository pattern er vigtigt af flere grunde, især når det kommer til at opbygge skalerbare og vedligeholdelsesvenlige applikationer. Her er nogle af de vigtigste fordele:

##### Adskillelse af ansvar
Repository pattern adskiller dataadgangslogikken fra forretningslogikken i din applikation. Dette gør koden mere organiseret, lettere at forstå og vedligeholde. Forretningslogikken bliver ikke blandet sammen med komplekse databaseforespørgsler, hvilket gør det lettere at ændre én del uden at påvirke den anden.

##### Testbarhed
Ved at bruge repository pattern kan du nemt mocke dine repositories i enhedstests, hvilket gør det muligt at teste forretningslogikken uden at være afhængig af en faktisk database. Dette forbedrer testdækningen og gør det lettere at finde fejl tidligt i udviklingsprocessen.

##### Fleksibilitet
Repository pattern giver dig fleksibilitet til at ændre dataadgangsstrategien uden at ændre forretningslogikken. Hvis du f.eks. ønsker at skifte fra en fil til SQL-database, kan du blot ændre repository-implementeringen uden at skulle ændre resten af applikationen.

##### Centraliseret Dataadgang
Ved at centralisere dataadgangslogikken i repositories, bliver det lettere at håndtere komplekse datamanipulationer og forespørgsler. Det giver også en enkelt kilde til ændringer, hvilket reducerer risikoen for fejl og inkonsistenser i datahåndtering.

##### Genanvendelighed
Repository pattern gør det lettere at genbruge dataadgangslogikken på tværs af forskellige dele af applikationen eller i forskellige projekter. Dette sparer tid og indsats, når du udvikler nye funktioner eller arbejder på andre projekter med lignende behov.

## Header2
---



## Related Topics
---
- Link
- 

## Resources
---
- Link
- 

