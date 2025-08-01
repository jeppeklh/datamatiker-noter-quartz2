---
aliases:
  - Prototyper
  - Prototype
---

>[!tldr] Definition  
Prototyper er iterative modeller, hvor man hurtigt udvikler en tidlig version af systemet for at teste koncepter, indsamle brugerfeedback og raffinere krav og design.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=485&selection=19,0,19,10|p.449]]

## Fordele  
---
- Giver mulighed for tidlig og direkte brugerfeedback, hvilket hjælper med at identificere krav og problemer i de tidlige faser.  
- Fremmer kreativitet og innovation ved at lade udviklere eksperimentere med forskellige designkoncepter.  
- Reducerer risikoen for store fejl i den endelige løsning, da prototyperne fungerer som testversioner.

## Ulemper  
---
- Risiko for at fokus flyttes fra en solid arkitektur til overfladisk brugergrænseflade, hvis prototypen opfattes som det endelige produkt.  
- Kan føre til øgede omkostninger og tidsforbrug, hvis prototyperne ikke kasseres, men videreudvikles uhensigtsmæssigt.  
- Kræver en klar strategi for overgangen fra prototype til fuld implementering.

## Typer af Prototyper 
---
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=487&selection=6,0,6,19|p.451]]
### Throwaway Prototype 
I en throwaway prototype udvikles en midlertidig version af systemet for udelukkende at studere et bestemt aspekt af applikationen. Efter at have opnået den nødvendige indsigt, kasseres prototypen, og den endelige løsning skrives fra bunden. 
### Evolutionary Prototype 
En evolutionary prototype demonstrerer nogle af applikationens funktioner i en tidlig version. Efterhånden som projektet skrider frem, forfines og udvides prototypen med nye funktioner, indtil den udvikler sig til det færdige produkt. 
### Incremental Prototyping 
Incremental prototyping indebærer opbygning af en række separate prototyper, der hver især viser forskellige dele af den endelige applikations funktionalitet. Disse individuelle prototyper kombineres (eller deres kode integreres) for at danne den komplette løsning. Da prototypekoden bliver en del af det endelige produkt, skal der anvendes god programmeringspraksis, hvilket typisk gør processen langsommere end med throwaway prototyping. Denne metode kan desuden gøre det muligt for flere teams at arbejde parallelt på systemets forskellige komponenter, dog med krav om planlagt integration.