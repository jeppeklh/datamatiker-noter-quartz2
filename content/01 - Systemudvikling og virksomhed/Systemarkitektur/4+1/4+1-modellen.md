---
aliases:
  - 4+1
---
> [!tldr] Definition
4+1 Arkitekturmodellen er en metode til at beskrive og visualisere softwarearkitektur ved hjælp af fem perspektiver – fire hovedvisninger plus et ekstra scenarieperspektiv. 
>
Modellen fokuserer på at opdele arkitekturen i forskellige aspekter for at imødekomme de forskellige interessenters behov.
[[4+1view-architecture.pdf#page=1&selection=44,0,44,22|4+1 p.1]]

## Formål og Anvendelse
---
- **Adresserer alle interessenters behov:** Modellen sikrer, at både slutbrugere, udviklere, systemingeniører og projektledere får indsigt i arkitekturen ud fra deres unikke perspektiv.
- **Forbedrer kommunikation og dokumentation:** Ved at opdele arkitekturen i separate visninger bliver det nemmere at diskutere, udvikle og vedligeholde komplekse systemer.
- **Understøtter både funktionelle og ikke-funktionelle krav:** Den dækker alt fra systemets funktionalitet til ydeevne, tilgængelighed og skalérbarhed.

## Struktur
---
Modellen er opdelt i følgende visninger:
- [[Logisk Visning]] – Beskriver systemets objektorienterede struktur og funktionelle krav.
- [[Procesvisning]] – Fokuserer på samtidighed, kommunikationsmønstre og systemets dynamiske adfærd.
- [[Udviklingsvisning]] – Omhandler den statiske organisering af softwaren i moduler og subsystems.
- [[Fysisk Visning]] – Viser mappingen af softwarekomponenter til hardware og netværksinfrastruktur.
- [[Scenarievisning]] – Anvender realistiske scenarier til at validere og illustrere, hvordan de øvrige visninger interagerer.

Ved at kombinere disse visninger giver 4+1 modellen en struktureret fremstilling af softwarearkitekturen, der både dækker overordnede designbeslutninger og de praktiske detaljer i implementeringen.

## Iterativ arkitekturudvikling
---
[[4+1view-architecture.pdf#page=13&selection=10,0,10,17|4+1 p.13]]
- Arkitekturen udvikles og forfines løbende gennem prototyping, testning og evaluering af scenarier. 
- Scenarierne hjælper med at identificere og validere de arkitektoniske elementer i alle visninger. 

## Dokumentation 
---
[[4+1view-architecture.pdf#page=14&selection=20,0,20,28|4+1 p.14]]
- En Software Architecture Document struktureres ofte efter de 4+1 visninger. 
- Dokumentationen indeholder blandt andet beskrivelse af mål, begrænsninger, og de specifikke elementer i hver visning. 

## Sammenhæng og tilpasning 
---
[[4+1view-architecture.pdf#page=10&selection=16,0,16,32|4+1 p.10]]
- Visningerne er forbundne – beslutninger i én visning påvirker de andre. 
- Modellen kan tilpasses: Ved små systemer kan visse visninger (f.eks. fysisk eller proces) udelades, hvis de ikke er relevante.


## Fleksibilitet og Iteration
---
Ved at anskue systemet fra flere perspektiver bliver det tydeligt, at der er behov for en metode, der både tillader en stærk arkitektonisk planlægning og samtidig muliggør iterative justeringer.

- **Agile metoder** kan drage fordel af 4+1 ved at iterativt udvikle og validere hvert perspektiv (f.eks. ved løbende at revidere use-cases og komponentintegration).
- **Traditionelle (vandfalds-)metoder** lægger større vægt på en fuldstændig upfront arkitektur, hvor alle 4+1 perspektiver detaljeres før udviklingen går i gang.
## Kommunikation og Samarbejde
---
En multi-perspektiv tilgang (som 4+1) fremmer en fælles forståelse blandt udviklere, arkitekter og interessenter. Dette understøtter metoder, hvor løbende kommunikation er central – uanset om det er via regelmæssige reviews i agile sprint eller gennem formaliserede design-gennemgange i mere traditionelle metoder.

## Risiko- og Ændringshåndtering
---
Ved at have flere “vinkler” på systemet kan fejl eller misforståelser opfanges tidligere i processen. Dette er afgørende for valg af metode, da en metode med indbygget feedback (som agile) ofte er bedre egnet til at håndtere de uundgåelige ændringer, der sker i komplekse systemer.

## Eksempler
---
> [!example] Eksempel
>Forestil dig et telefonsystem (f.eks. et PABX-system) som et konkret eksempel: 
>- **Overordnet:** Systemet skal kunne håndtere ind- og udgående opkald, dirigere forbindelser, og sikre, at alle telefoner kommunikerer effektivt. 
>- **Behov:** Slutbrugere vil se et simpelt brugerinterface, mens udviklere og systemingeniører skal forstå, hvordan opkaldene styres i baggrunden, hvordan processerne kører parallelt, og hvordan systemet deployeres på fysisk hardware.

>[!example] Logisk visning
  >- **Hvad den dækker:** Den statiske struktur af systemet – f.eks. hvilke klasser og objekter der er involveret, og hvordan de relaterer til hinanden. 
  >- **Eksempel:** En domænemodel, der viser telefonen, forbindelsescontrolleren, nummerplanen og de relationer, der binder disse sammen.

>[!example] Procesvisning
>- **Hvad den dækker:** Den dynamiske adfærd og samtidigheden i systemet – hvordan opkald behandles, og hvordan systemets processer kører parallelt. 
>- **Eksempel:** Et diagram, der illustrerer, hvordan separate processer (f.eks. et opkalds-håndteringsmodul og et signalbehandlingsmodul) kommunikerer via beskeder eller RPC for at etablere og vedligeholde en opkaldsforbindelse.

> [!example] Udviklingsvisning
>- **Hvad den dækker:** Organiseringen af softwaren i moduler og subsystems – hvordan koden er struktureret, og hvordan udviklingsteamet opdeler arbejdet. 
>- **Eksempel:** Et moduldiagram, der viser opdelingen af koden i forskellige lag og biblioteker, f.eks. et lag til netværkskommunikation, et lag til opkaldslogik, og et lag til brugerinterface.

> [!example] Fysisk Visning
>- **Hvad den dækker:** Mapping af softwarekomponenter til hardware – hvordan systemets processer fordeles på servere, netværk og andre fysiske enheder. 
>- **Eksempel:** Et diagram, der viser, hvordan de logiske og processuelle komponenter i telefonsystemet deployeres på forskellige maskiner (f.eks. primære og backup-servere, routere og gateways).

> [!example] Scenarievisning (+1)
>- **Hvad den dækker:** Realistiske brugsscenarier, der illustrerer hvordan de forskellige visninger arbejder sammen i praksis. 
>- **Eksempel:** Et sekvensdiagram for en typisk opkaldsproces, der viser, hvordan telefonens controller registrerer en brugerhandling, hvordan opkaldet oprettes, og hvordan forbindelsen etableres gennem de logiske, processuelle og fysiske lag.
