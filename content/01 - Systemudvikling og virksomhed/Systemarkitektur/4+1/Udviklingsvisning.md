
> [!tldr] Formål
>At vise den statiske organisering af softwaren i form af moduler, biblioteker og subsystems, hvilket understøtter udviklingsprocessen.
[[4+1view-architecture.pdf#page=6&selection=41,0,41,28|4+1 p.6]]

Hvordan udviklingsteamet opdeler arbejdet (fx modulopdeling, versionering, frameworks), som afspejles i både high-level og low-level design. Denne visning understøtter et struktureret samarbejde og kodningsstandarder.
## Kerneelementer
---
- **Modulstruktur:** Opdeling af koden i små, håndterbare enheder såsom moduler og subsystems.
- **Lagdeling:** Organisering i lag med veldefinerede ansvarsområder, der reducerer komplekse afhængigheder.
- **Afhængigheder:** Beskrivelse af import- og eksportrelationer, som styrer synligheden og interaktionen mellem moduler.

## Anvendelse
---
- Understøtter planlægning, teamorganisering, og vedligeholdelse af softwaren ved at skabe et klart overblik over kodestrukturen.

> [!example] Eksempel
Forestil dig et modulært opbygget system til online bestilling:
>- **Brugergrænseflade:** Ansvarlig for visning af produkter og interaktion med brugeren.
>- **Forretningslogik:** Håndterer ordredannelse, prisberegning og rabatter.
>- **Dataadgangslag:** Kommunikerer med databasen for at hente og gemme data.
>- **Integrationer:** Moduler der forbinder systemet med eksterne betalingsgateways og forsendelsessystemer.
>
Et moduldiagram vil vise, hvordan disse lag og moduler er struktureret og afhænger af hinanden, med tydelige grænseflader, hvilket letter udvikling, vedligeholdelse og test.
