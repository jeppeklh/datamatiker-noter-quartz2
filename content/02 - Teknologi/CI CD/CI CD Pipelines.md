tags: #C-sharp #Programmering

## Definition 
--- 
Der er otte grundlæggende elementer i CI/CD, som hjælper med at sikre maksimal effektivitet i din udviklingscyklus. 

De dækker både udvikling og implementering. Inkluder disse grundprincipper i din pipeline for at forbedre din DevOps-arbejdsgang og softwarelevering:

### Ét samlet kildekode-repository  
---
Source code management (SCM), der indeholder alle nødvendige filer og scripts til at skabe builds, er afgørende. 
Repositoriet skal indeholde alt, der er nødvendigt for build-processen. 
Dette inkluderer kildekode, databasestruktur, biblioteker, properties-filer og versionskontrol. Det skal også indeholde test-scripts og scripts til at bygge applikationer.

### Hyppige check-ins til main branch
---
Integrér kode i trunk, mainline eller master branch — dvs. trunk-based development — tidligt og ofte. 
Undgå sub-branches og arbejd kun med main branch. 
Brug små kodestykker og merge dem i branchen så hyppigt som muligt. 
Merge ikke mere end én ændring ad gangen.

### Automatiserede builds 
---
Scripts bør indeholde alt, der er nødvendigt for at bygge med en enkelt kommando. 
Dette inkluderer webserverfiler, databasescripts og applikationssoftware. CI-processer skal automatisk pakke og kompilere koden til en anvendelig applikation.

### Selvtestende builds  
---
CI/CD kræver kontinuerlig testning. 
Testscripts bør sikre, at en testfejl resulterer i en fejlet build. 
Brug statiske pre-build testscripts til at kontrollere koden for integritet, kvalitet og sikkerhedsoverholdelse. 
Kun kode, der består statiske tests, bør inkluderes i buildet.

### Hyppige iterationer  
---
Flere commits til repositoriet resulterer i færre skjulte konflikter. 
Lav små, hyppige iterationer i stedet for store ændringer. 
På denne måde er det nemt at rulle ændringer tilbage, hvis der opstår et problem eller en konflikt.

### Stabile testmiljøer  
---
Koden bør testes i en klonet version af produktionsmiljøet. Du kan ikke teste ny kode i den live produktionsversion. 
Opret et klonet miljø, der er så tæt som muligt på det reelle miljø. 
Brug strenge testscripts til at opdage og identificere fejl, der er sluppet gennem den indledende pre-build testproces.

### Maksimal synlighed  
---
Alle udviklere bør have adgang til de nyeste eksekverbare filer og kunne se eventuelle ændringer i repositoriet. 
Informationen i repositoriet bør være synlig for alle. 
Brug versionskontrol til at styre overleveringer, så udviklerne ved, hvilken version der er den nyeste. 
Maksimal synlighed betyder, at alle kan overvåge fremskridt og identificere potentielle problemer.

### Forudsigelige implementeringer når som helst 
---
Implementeringer bør være så rutineprægede og risikofri, at teamet er trygge ved at udføre dem når som helst. 
CI/CD-test- og verifikationsprocesser bør være strenge og pålidelige, hvilket giver teamet tillid til at implementere opdateringer på ethvert tidspunkt. 
Hyppige implementeringer, der inkluderer begrænsede ændringer, udgør også lavere risici og kan nemt rulles tilbage.


## Related Topics
---
- Link
- 

## Resources
---
- [CI/CD Pipelines](https://about.gitlab.com/topics/ci-cd/)
- 