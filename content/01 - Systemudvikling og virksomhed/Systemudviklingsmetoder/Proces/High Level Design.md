---
aliases:
  - HLD
---
>[!tldr] Definition
High Level Design (HLD) har til formål at sikre en fælles konceptuel forståelse af systemet, særligt med fokus på, hvordan systemet præsenteres og opleves af brugerorganisationen og Product Owner. 
>
I HLD fokuserer du på det overordnede design og modelleringen af systemet, hvor det betragtes som en "blackbox" – du kigger på input, output og de overordnede interaktioner, uden at dykke ned i interne detaljer.

---

## Formålet
---
Formålet med HLD er at:

- Sikre en fælles konceptuel forståelse af systemet
- Udføre designaktiviteter rettet mod brugerorganisationen/Product Owner
- Beskrive de konceptuelle mønstre og overordnede systemvalg, herunder valg af arkitektur og hvilke elementer, der indgår i systemet

Når du arbejder med HLD, er det vigtigt at fokusere på det overordnede design og modellering, således at systemet præsenteres som en "black box" – du behøver ikke vide, hvad der sker inde i kassen, men du skal forstå, hvordan brugeren interagerer med systemet.



## Systemet som Black Box
---
I High Level Design fremstiller du artefakter, der:

- Viser, hvordan brugeren interagerer med systemet
- Angiver, hvilken information der benyttes i systemet

Processen for HLD indebærer, at du går fra konkrete eksempler på, hvordan systemet skal anvendes, til mere generiske beskrivelser, diagrammer og modeller. Denne transformation fra det specifikke til det abstrakte hjælper med at afdække de overordnede konceptuelle mønstre.

**Brugerfokus:**  
Dit primære fokus er på brugeroplevelsen. Dokumentationen skal derfor udarbejdes på domænesproget – det sprog og de begreber, som brugeren benytter. For eksempel kan termer som *klient*, *kunde*, *bruger* eller *patient* have meget forskellige betydninger afhængigt af konteksten, så det er essentielt at afklare disse begreber i samarbejde med brugerne.


## Kvalitetssikring af High Level Design
---
For at sikre, at HLD lever op til sine formål, skal du have fokus på to hovedaspekter:

### 1. Laver du det rigtige system?
- **Sporbarhed:**  
  Dine artefakter skal altid kunne spores tilbage til kravindsamlingen. Det skal være tydeligt, hvordan de overordnede designvalg bygger på de indsamlede krav. Denne sporbarhed er essentiel for at dokumentere, at du har dækket de relevante behov og krav fra starten.

### 2. Laver du systemet rigtigt?
- **Kvaliteten af det enkelte artefakt:**  
  Hvert artefakt, du producerer, skal udarbejdes på en måde, der sikrer brugbare og fagligt korrekte løsninger. Det betyder, at du skal fastsætte kvalitetskriterier for hvert artefakt ud fra de metoder og teknikker, du har valgt. Disse kriterier skal understøtte, at artefakterne lever op til både de tekniske og brugercentrerede krav, der er identificeret.

---

Ved at holde fokus på både sporbarheden til kravindsamlingen og kvaliteten af de enkelte artefakter, sikrer du, at High Level Design fungerer som en solid basis for den videre udviklingsproces – og at systemet bliver designet, så det møder brugerens forventninger og behov.


## Ting man typisk specificerer i HLD
---
#### Security
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=155&selection=31,0,31,8|p.119]]
Overvejelser om 
- Bugs
- Intentional Attacks
- Tilfældige fejl (Miste en laptop eller flashdrive med backups)

Kan løses med backups af
- Projektdokumentation
- Source code
- Data
- Etc.

#### Hardware
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=156&selection=14,0,14,8|p.120]]
- Operativsystemer
- Programmeringssprog
- Printere
- Netværkskomponenter (modem, gateways, routers)
- Servers
#### User Interface
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=157&selection=6,0,6,14|p.121]]
- Beskrivelse af basic navigationstil [[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=157&selection=10,36,11,49|p.121]]
- Beskrivelse af specielle feature (clickable maps, vigtige tabeller) [[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=157&selection=25,63,28,55|p.121]]
#### Internal Interfaces
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=158&selection=23,0,23,19|p.122]]

#### External Interfaces
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=159&selection=0,15,10,19|p.123]]

## Resourser
---
- [Fokusområde Læringsobjekt (HLD)](https://rise.articulate.com/share/C9x7c641Qf8pDgT76Nqqy6ykP99dRgRJ#/lessons/Nxgu0fFoU7w9sR5J0Dc4Bnhr4rnt9bcE)