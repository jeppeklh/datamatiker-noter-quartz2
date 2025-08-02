---
aliases:
  - IaC
---
> [!tldr] Definition
> Evnen til at provisionere og supportere din computerinfrastruktur via kode. I stedet for at skulle konfigurere hver server, netværk eller lagringsenhed manuelt, beskrives miljøet med kode.
    
- **Baggrund:**  
    Hver applikationsinfrastruktur omfatter mange elementer såsom operativsystemer, databaseforbindelser og lagring. Manuelle konfigurationsprocesser er tidskrævende og fejlbehæftede – specielt ved skalering.
    
- **Formål:**  
    Med IaC kan du definere den ønskede tilstand for miljøet, og en automatiseret proces sørger for at realisere denne tilstand. Dette giver udviklerne mulighed for at fokusere på at bygge og forbedre applikationer i stedet for at bruge tid på miljøopsætning.
    
---

## Fordele ved IaC
- **Automatisering af Infrastruktur:**
    - Opsætning af komplekse miljøer automatiseres, hvilket reducerer både manuelle processer og risikoen for fejl.
    - Eksempel: Kopiering af hele et regionalt kontormiljø med et enkelt kodeuddrag, hvilket sikrer konsistens på tværs af lokationer.

- **Fejlreduktion og Konsistens:**
    - Mindsker risikoen for menneskelige fejl og "configuration drift", hvor miljøer afviger fra hinanden.
    - Muligheden for hurtigt rollback til en tidligere, kendt stabil version af konfigurationsfilerne.

- **Skalerbarhed og Fleksibilitet:**
    - Nem duplikering af miljøer – fx til udvikling, test og produktion – ved at bruge samme IaC-kode.
    - Giver mulighed for hurtig respons på nye forretningsmuligheder ved at oprette nye miljøer inden for minutter.

- **Understøtter Versionsstyring:**
    - IaC-filer kan gemmes i et versionsstyringssystem (som Git), hvilket muliggør transparens og samarbejde ved kodeændringer.
    - Udviklere kan branche og iterere på miljøkonfigurationer ligesom applikationskode.

---

## Sådan virker IaC
- **Kodebaseret Infrastrukturstyring:**
    - Ligesom applikationskode beskriver IaC et system og dets arkitektur – fra servere og netværk til lagring og operativsystemer.
    - Konfigurationsfiler fungerer som kildekode, som man kan udvikle og vedligeholde i et IDE (Integrated Development Environment) med indbygget fejlcheck.

- **Automatiseret Deployment:**
    - Ved at køre IaC-kode kan du provisionere og konfigurere ressourcer automatisk og gentageligt.
    - Eksempel: En IaC-skabelon, der opretter en komplet webapplikationsinfrastruktur i skyen med alt fra virtuelle maskiner til netværksindstillinger.

- **Integration med CI/CD:**
    - IaC kan integreres direkte i CI/CD-pipelines, så ændringer i infrastrukturen deployeres sammen med applikationsopdateringer.
    - Dette sikrer, at miljøerne hele tiden er konsistente og deploybare.

---

## Tilgange til IaC
### Declarative Approach

- **Beskrivelse:**
    - Du beskriver _hvad_ sluttilstanden for miljøet skal være, ikke nødvendigvis _hvordan_ man kommer dertil.
    - Forudsætter at systemets komponenter og indstillinger er kendt – løsningen sørger for at skabe denne tilstand.

- **Fordele:**
    - Enkel at forstå og bruge, når miljøets krav er klare.

- **Eksempel:**
    - En Terraform-konfiguration, hvor du definerer de nøjagtige ressourcer (fx en VM, database og netværk) og deres ønskede tilstand.

---

### Imperative Approach
- **Beskrivelse:**
    - Du beskriver _hvordan_ miljøet skal bygges op, dvs. alle de trin og kommandoer, der skal køres for at opnå den ønskede tilstand.
    - Relevant i komplekse scenarier, hvor rækkefølgen af operationer er kritisk.

- **Fordele:**
    - Mere fleksibel i miljøer med komplekse installations- og konfigurationskrav.

- **Eksempel:**
    - Et script (fx i Bash eller PowerShell) der sekventielt opsætter en server, installerer nødvendige pakker og konfigurerer netværksindstillinger.

---

## IaC og DevOps
- **Integration i DevOps:**
    - IaC er en central komponent i DevOps, hvor man søger at automatisere hele livscyklussen for applikationsudrulninger.
    - DevOps-teams integrerer IaC i deres CI/CD-pipelines for at sikre at miljøændringer sker samtidig med kodeændringer.

- **Fordele for DevOps:**
    - Hurtig opsætning af komplette miljøer – fra udvikling til produktion.
    - Sikrer reproducerbare og konsistente miljøer, hvilket mindsker risikoen for fejl ved deployment.
    - Muliggør en fælles “sprogbrug” mellem udviklings- og operationsteams, da begge parter kan gennemgå og versionstyre infrastrukturkoden.

- **Eksempel:**
    - Når en udvikler foretager et commit med ændringer i både applikationskode og IaC-skabeloner, udløses en CI-pipeline, som samtidig bygger applikationen og provisionerer et opdateret miljø – dette skaber hurtig feedback og reducerer risikoen for at deployment-skabeloner afviger fra applikationskoden.

---

## Opsummering
Infrastructure as Code (IaC) muliggør:

- **Automatiseret og fejlfri infrastrukturstyring**
    - Reducerer tidsforbruget og risikoen for fejl gennem kode-baseret provisioning.

- **Konsistente og skalerbare miljøer**
    - Sikrer, at ensartede miljøer kan oprettes hurtigt på tværs af forskellige lokationer med en enkelt IaC-kodebase.

- **Sammenhæng med DevOps-praksisser**
    - Understøtter CI/CD ved at integrere miljøændringer direkte i udrulningsprocessen og sikre, at alle teams arbejder ud fra de samme konfigurationsfiler.


Ved at anvende både deklarative og imperative tilgange kan virksomheder tilpasse IaC til deres specifikke behov og komplekse infrastrukturscenarier. Denne praksis reducerer ikke kun administrative byrder, men skaber desuden et mere robust og skalerbart it-miljø, som understøtter hurtige forretningsmæssige ændringer og innovation.

---

## Resourcer
- [aws IaC](https://aws.amazon.com/what-is/iac/)