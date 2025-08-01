
tags: #C-sharp #Programmering

## Definition 
---
Systemudviklingsmetode
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=493&selection=10,0,10,15|Rod Stevens p.457]]
Objektorienteret analyse, design og programmering
Iterativ

Unified Process (UP) er en iterativ softwareudviklingsproces til opbygning af objektorienterede systemer 
> ([[applying-uml-and-patterns-3rd.pdf#page=56&selection=0,38,56,18|Larman p.56]])

Den er kendt for sin fleksibilitet og åbenhed, og den opfordrer til at inkorporere effektive praksisser fra andre iterative metoder såsom Extreme Programming (XP) og Scrum.
> ([[applying-uml-and-patterns-3rd.pdf#page=56&selection=33,0,56,18|Larman p.56]])


![[UnifiedProcess.png]]
## Iterativ og evolutionær udvikling
---
Kernen i UP, og de fleste andre moderne metoder, er iterativ udvikling. Denne livscyklustilgang organiserer udviklingen i en række korte, fastlagte mini-projekter kaldet iterationer.
([[applying-uml-and-patterns-3rd.pdf#page=57|Larman p.57]])

- Hver iteration resulterer i et testet, integreret og eksekverbart delsystem.

- Hver iteration inkluderer sine egne krav analyse, design, implementering og testaktiviteter.

- Iterationer varer typisk mellem to og seks uger.
([[applying-uml-and-patterns-3rd.pdf#page=214&selection=18,1,20,53|Larman p.214]])

- Kortere iterationer foretrækkes, medmindre teamet er meget stort.
([[applying-uml-and-patterns-3rd.pdf#page=214&selection=18,1,20,53|Larman p.214]])

Denne iterative tilgang er evolutionær, da kravene og designet ikke er færdigdefineret før implementeringen, men i stedet tilpasser sig og udvikler sig gennem feedback i løbet af iterationerne.

## Agile principper i UP
---
UP er designet til at være fleksibel og kan anvendes i en agil tilgang, der inkluderer praksisser fra andre agile metoder78. En agil UP fokuserer på:


- Et lille sæt af UP-aktiviteter og artefakter9.

- Tidlig programmering fremfor tidlig dokumentation
([[applying-uml-and-patterns-3rd.pdf#page=74&selection=15,0,29,22|Larman p.74]])

- Tilpasning af processen til projektets behov.

## UP faser
---
UP-projekter organiserer arbejdet og iterationer på tværs af fire hovedfaser:

1. Inception: Formål, forretningsgrundlag, omfang og usikre estimater defineres.

2. Elaboration: Forfinet vision, implementering af kernearkitekturen, løsning af højrisikoelementer, identifikation af de fleste krav og omfang, mere realistiske estimater.

3. Construction: Implementering af resterende elementer med lavere risiko, forberedelse til udrulning10.

4. Transition: Udrulning af systemet til produktion, overgang til driftsmiljø.
([[applying-uml-and-patterns-3rd.pdf#page=77&selection=0,0,22,23|Larman p.77]])

## UP discipliner
---
UP beskriver arbejdsaktiviteter indenfor discipliner - et sæt af relaterede aktiviteter og artefakter inden for et emneområde, f.eks. krav analyse11. Nogle af de vigtigste discipliner er:

- **Business Modeling**: Visualisering af koncepter i applikationsdomænet med Domain Model-artefaktet.

- **Requirements**: Indsamling af funktionelle og ikke-funktionelle krav med Use-Case Model og Supplementary Specification-artefakter.

- **Design**: Design af softwareobjekter med Design Model-artefaktet.

Arbejdsindsatsen fordeles forskelligt på tværs af disciplinerne i løbet af projektet. Tidlige iterationer fokuserer typisk mere på krav og design, mens senere iterationer fokuserer mere på implementering.

## Tilpasning af UP
---
UP er meget tilpasningsdygtig, og næsten alle aktiviteter og artefakter er valgfri15. Hvert projekt skal skræddersy UP til sine specifikke behov ved at vælge de aktiviteter og artefakter, der giver mest værdi.

Fordele ved UP:

- **Iterativ og evolutionær**: Giver mulighed for løbende feedback og tilpasning, hvilket minimerer risikoen for at udvikle et system, der ikke møder brugernes behov.

- **Agile og fleksibel**: Kan tilpasses til forskellige projekttyper og -størrelser og understøtter integration af praksisser fra andre agile metoder.

- **Fokus på arkitektur**: Sætter fokus på tidlig identifikation og stabilisering af systemets arkitektur, hvilket er afgørende for systemets kvalitet og vedligeholdelse.

- K**ontinuerlig kvalitetssikring:** Fremmer tidlig og hyppig testning for at sikre høj kvalitet og identificere problemer tidligt i processen.

- **Brugerinvolvering**: Opfordrer til løbende brugerinvolvering for at sikre, at systemet opfylder deres behov og forventninger.

![[UnifiedProcessWithDetails.png]]

## Related Topics
---
- Link
- 

## Resources
---
- Link
- 