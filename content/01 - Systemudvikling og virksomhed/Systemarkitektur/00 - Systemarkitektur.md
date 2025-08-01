---
aliases:
  - Systemarkitektur
  - System Architecture
---
> [!tldr] Definition
Systemarkitektur beskriver, hvordan en applikations dele passer sammen på et 'high level'. Arkitekturen fastlægger de overordnede strukturer og de standardiserede mønstre, som udviklere kan anvende for at løse specifikke problemer.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=160&selection=14,0,14,12|p.124]]


## Overblik
---
  En applikations arkitektur viser, hvordan de enkelte dele (moduler, komponenter, tjenester) integreres og kommunikerer for at levere applikationens funktionalitet.

- **Formål:**  
  - At forenkle udvikling og vedligeholdelse.
  - At minimere afhængigheder mellem systemets dele.
  - At tilpasse arkitekturen til de specifikke krav og problemstillinger, som applikationen skal løse.


## Almindelige Arkitekturtyper
---
- [[Monolitisk Arkitektur]]
- [[Client-Server Arkitektur]]
- [[Multitier Arkitektur]]
- [[Component-based Arkitektur]]
- [[Service-Oriented Arkitektur]]
- [[Data-Centric Arkitektur]]
- [[Event-Driven Architecture|Event-Driven Arkitektur]]
- [[Rule-Based Arkitektur]]
- [[Distributed Arkitektur]]

## Mix and Match
---
  Et system behøver ikke at følge én enkelt arkitektur. Forskellige dele af applikationen kan implementeres med forskellige arkitektoniske tilgange for at opfylde specifikke krav.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=168&selection=31,0,31,13|p.132]]

> [!example] Eksempel
  Et [[Repo/04 - Opgaver/Teknologi/Distribuerede Systemer|distribueret]], service-orienteret system, der benytter komponentbaserede tjenester og [[Multitier Arkitektur|multitier]]-strukturer.

## Eksempel
---
> [!example] Eksempel: Valg af Arkitektur til ClassyDraw
Forestil dig, at du skal vælge en arkitektur til **ClassyDraw** – en tegneapplikation som minder om MS Paint, men hvor brugeren kan vælge og manipulere tegneobjekter. Her er en forenklet gennemgang af forskellige arkitekturtyper og, om de vil give mening for dette program:
>
>- **[[Monolitisk Arkitektur]]:**  
  Standardløsningen, hvor hele applikationen er samlet i ét program. Dette er ofte nok for simple applikationer og kan fungere fint, hvis ingen af de mere avancerede arkitekturtyper er nødvendige.
>
>- **[[Client-Server Arkitektur|Klient/Server]] og [[Multitier Arkitektur|multitier]]:**  
  Disse arkitekturer opdeler systemet, fx med en brugergrænseflade (klient) og en separat datahåndtering (server). Da ClassyDraw gemmer tegninger som filer (ikke i en database), er denne opdeling ikke nødvendig for en simpel tegneapplikation.
>
>- **[[Component-based Arkitektur]]:**  
  Her opdeles applikationen i separate komponenter, der leverer tjenester til hinanden – for eksempel en "Rektangel-komponent" til at tegne rektangler. For ClassyDraw er det dog ofte lige så nemt at bruge en simpel klasse i stedet for at opdele programmet i mange små, løst koblede komponenter.
>
>- **[[Service-Oriented Arkitektur]]:**  
  Denne tilgang deler applikationen op i selvstændige tjenester, der kan køre på forskellige maskiner via webtjenester. For en simpel tegneapplikation vil det dog være overflødigt og unødigt komplicere designet.
>
>- **[[Data-Centric Arkitektur]]:**  
  En data-centreret arkitektur fokuserer på håndtering af et centralt datasæt, ofte i form af en database. I ClassyDraw definerer brugeren selv tegningerne, så der er ikke et fast datasæt at organisere programmet omkring.
>
>- **[[Event-Driven Architecture|Event-Driven Arkitektur]]:**  
  I en event-drevet arkitektur reagerer brugergrænsefladen på brugerens handlinger – fx når brugeren vælger et værktøj og klikker eller trækker for at oprette eller flytte en figur. Dette er en naturlig tilgang for en tegneapplikation.
>
>- **[[Rule-Based Arkitektur]]:**  
  Her styres programmet af et sæt regler, der bestemmer, hvad der skal ske ud fra specifikke input. Da der ikke er faste regler for, hvordan man skal tegne (brugeren har friheden til at skabe, som vedkommende ønsker), er denne metode ikke relevant for ClassyDraw.
>
>- **[[Distributed Arkitektur]]:**  
  En distribueret arkitektur fordeler opgaver over flere processorer eller maskiner, hvilket kan være fordelagtigt for beregningstunge applikationer. Da ClassyDraw ikke udfører omfattende beregninger, vil en distribueret arkitektur sandsynligvis ikke give nogen fordel.
>
**Konklusion:**  
Da ingen af de mere komplekse arkitekturtyper (fx klient/server, service-orienteret eller distribueret) er nødvendige for en simpel tegneapplikation, er den mest hensigtsmæssige løsning for ClassyDraw en **[[Monolitisk Arkitektur|monolitisk Arkitektur]] med en [[Event-Driven Architecture|event-drevet]] brugergrænseflade**.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=168&selection=45,0,45,23|p.132]]

## Konklusion
---
Valget af systemarkitektur afhænger af applikationens krav, størrelse og de teams, der skal udvikle og vedligeholde systemet. En gennemtænkt arkitektur sikrer:

- **Fleksibilitet:** Nem tilpasning og udskiftning af komponenter.
- **Skalerbarhed:** Evnen til at vokse og håndtere flere brugere eller data.
- **Vedligeholdelighed:** Reduceret kompleksitet ved opdateringer og fejlrettelser.

En god systemarkitektur udgør fundamentet for en robust, effektiv og fremtidssikret applikation.

## Resourcer
---
- [System Architecture LinkedIn](https://www.linkedin.com/learning/software-architecture-foundations/what-s-the-job-traditional-architects?resume=false&u=57075649)