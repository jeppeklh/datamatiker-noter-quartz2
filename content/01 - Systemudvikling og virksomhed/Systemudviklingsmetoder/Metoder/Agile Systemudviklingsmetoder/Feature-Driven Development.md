---
aliases:
  - FDD
  - Feature Driven Development
---
>[!tldr] Definition
> **Feature-Driven Development (FDD)** er en iterativ og inkrementel udviklingsmetode designet til store team. FDD fokuserer på at bygge applikationen gennem en liste af konkrete funktioner ("features"), der implementeres trin for trin. 
>
> [[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=536&selection=75,0,76,19|p.500]]

---

## Nøgleegenskaber
- **Feature-fokuseret**: Funktioner er små, klart definerede handlinger (fx "Beregn kundes saldo").
- **Storskala venlig**: Egnet til store team og komplekse projekter.
- **Struktureret proces**: 5 faser og 6 milepæle for at sikre orden.
- **Korte iterationer**: Hver funktion implementeres på max 2 uger.

---

## Roller i FDD

| **Rolle**               | **Ansvar**                                                                 |
|--------------------------|----------------------------------------------------------------------------|
| **Project Manager**      | Administrerer budget, tidsplan og ressourcer.                              |
| **Chief Architect**      | Hovedansvarlig for systemets overordnede design.                           |
| **Development Manager**  | Håndterer daglig udvikling og løser konflikter.                            |
| **Chief Programmers**    | Erfarne udviklere, der leder feature-teams og designinspektioner.          |
| **Class Owners**         | Udviklere, der ejer specifikke klasser og samarbejder i feature-teams.     |
| **Domain Experts**       | Faglige eksperter (fx brugere), der definerer funktioners formål.          |
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=537&selection=13,0,13,9|p.501]]
*Andre roller inkluderer Build Engineer, Deployer og Technical Writer.*

---

## Faser i FDD
1. **Develop a Model**  
   - Opret et overblik over systemet via en objektmodel i samarbejde med domæneeksperter.

2. **Build a Feature List**  
   - Opdel funktioner i et hierarki: *Område → Aktivitet → Feature* (fx "Ordrehåndtering → Opret ordre → Beregn subtotal").

3. **Plan by Feature**  
   - Prioriter funktioner og tildel dem til chief programmers/teams baseret på objektmodellen.

4. **Design by Feature**  
   - Feature-teamet (class owners) designer funktionen via sekvensdiagrammer og metode-prologer.  
   - **Designinspektion** sikrer kvalitet før kodning.

5. **Build by Feature**  
   - Kode, test og integrer funktionen. Chief Programmer gennemfører kodeinspektion.

[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=538&selection=44,0,44,10|p.502]]

---

## Milepæle i Iterationer
Hver iteration (max 2 uger) har 6 milepæle med **procentfordeling**:

| **Milepæl**               | **Beskrivelse**                          | **Færdiggørelse** |
|---------------------------|------------------------------------------|-------------------|
| Domain Walkthrough         | Valgfri gennemgang med domæneekspert     | 1%                |
| Design                     | Udvikling af sekvensdiagrammer           | 40%               |
| Design Inspection          | Godkendelse af design                    | 3%                |
| Code                       | Implementering af kode                   | 45%               |
| Code Inspection            | Godkendelse af kode                      | 10%               |
| Promote to Build           | Integration i hovedsystem                | 1%                |

*Designfasen udgør 40% – understreger dens betydning for store projekter.*
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=540&selection=69,0,69,24|p.504]]

---

## Fordele vs. Udfordringer

| **Fordele**                          | **Udfordringer**                                |
| ------------------------------------ | ----------------------------------------------- |
| Klart definerede roller og processer | Kompleks struktur kan føles rigid for små teams |
| God til store team                   | Kræver erfaren ledelse (Chief Programmers)      |
| Transparent fremskridt via milepæle  | Dokumentationsbyrde (designpakker, prologer)    |
| Mindrer risiko gennem inspektioner   | Begrænset fleksibilitet i ændrede krav          |
