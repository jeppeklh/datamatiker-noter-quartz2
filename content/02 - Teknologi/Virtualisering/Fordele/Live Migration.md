> [!tldr] Definition
Overførsel af en virtuel maskines data – såsom hukommelse og kørselsstatus – fra en host til en anden, mens maskinen fortsætter med at køre. 
Dette muliggør, at hvis en host skal tages offline (for eksempel til vedligeholdelse eller på grund af problemer), kan de virtuelle maskiner flyttes til en anden host uden nedetid.

- **Fordele:**
  - **Minimeret nedetid:** Brugerne bemærker som regel ikke, at migrationen finder sted.
  - **Fleksibilitet:** Systemadministratoren kan planlægge vedligeholdelse eller reagere på hardwareproblemer uden at afbryde driften.
  
- **Udfordringer og Overvejelser:**
  - **Overførselstid:** Tiden, der kræves for en live migration, afhænger af den virtuelle maskines størrelse og den tilgængelige båndbredde mellem de involverede hosts.
  - **Planlægning:** Live migration kan udføres manuelt af en administrator eller planlægges på forhånd. Avancerede systemer kan endda understøtte automatisk migration ved at overvåge hostens tilstand og igangsætte flytningen, hvis der opstår problemer.
  - **Optimering:** Ved at holde virtuelle maskiner små (f.eks. anvende den mindste harddiskstørrelse, der opfylder kravene) og sikre høj netværksbåndbredde, kan migrationsprocessen gøres hurtigere.
## Resourcer
---
- [Virtualisering LinkedIn Kursus (Fordele)](https://www.linkedin.com/learning/learning-virtualization-13945890/using-virtualization-to-increase-availability?autoSkip=true&resume=false&u=57075649)
- 