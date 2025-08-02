
>[!tldr] Definition
> **Lean Software Development** (Lean) er en [[Agile]]-tilgang, der fokuserer på at minimere spild og maksimere værdi for kunden. Metoden er inspireret af lean manufacturing (Toyota) og handler om at bygge kun det nødvendige – intet mere, intet mindre.
>
> [[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=530&selection=35,0,35,4|p.494]]

---

## Kerneprincipper
### 1. Eliminer Spild
- **Spild** er alt, der ikke direkte tilføjer værdi for kunden. 
Eksempler:  
  - Uklare krav  
  - Unødvendige features eller kode ("overengineering")  
  - Gentagen arbejde (fx manglende dokumentation)  
  - Unødvendige møder eller bureaukrati  

### 2. Respekter Teamet
- Giv teamet autonomi til at selvorganisere og træffe beslutninger.  
- Undgå mikro-management – tillid er nøglen.

### 3. Udsæt Forpligtelser
- Tag ikke beslutninger før nødvendigt. Undgå at "låse fast" på design/teknologier tidligt.  
- Eksempel: Vent med at vælge database, indtil krav til skalerbarhed er klare.

### 4. Lever Hurtigt
- Brug korte iterationer (1-4 uger) til hyppig leverance af funktionel software.  
- Mindre batches = hurtigere feedback og mindre risiko.

### 5. Byg Viden
- Lær kontinuerligt gennem prototyping, tidlig testning og kundesamarbejde.  
- Dokumenter erfaringer for at undgå at gentage fejl.

### 6. Indbyg Kvalitet
- Automatiser test og integration for at fange fejl tidligt.  
- Refaktorér løbende for at bevare kodekvalitet.

### 7. Se Det Hele
- Teamet skal forstå den **holistiske proces** (fra krav til leverance).  
- Undgå silo-tænkning – alle er ansvarlige for hele systemet.

[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=530&selection=59,0,59,15|p.494]]

---

## Lean vs. Traditonelle Metoder

| **Lean Fokus**                | **Traditionelt Fokus**          |
|-------------------------------|----------------------------------|
| Minimalt spild                | Fuldstændig dokumentation       |
| Fleksible krav                | Fastlåste krav fra start        |
| Kort feedback-loop            | Lange udviklingscyklusser       |

---

## Praktiske Teknikker
- **Value Stream Mapping**: Analyser processer for at identificere spild.  
- [[Kanban]]: Visualiser arbejdsflow og begræns "work in progress" (WIP).  
- **MVP (Minimum Viable Product)**: Lever kun kernesfunktioner først.

---

## Fordele & Udfordringer

| **Fordele**                          | **Udfordringer**                          |
|---------------------------------------|--------------------------------------------|
| Mindre risiko for overflødigt arbejde | Kræver disciplin til at holde fokus        |
| Hurtigere markedsadgang               | Svært at definere "nødvendigt" præcist     |
| Bedre kundetilpasning                 | Kan føles ustruktureret for nye teams      |

---

## Kombination med Andre Metoder
Lean kan kombineres med andre [[Agile]]-metoder:  
- [[SCRUM]]: Lean-principper til spildreduktion + Scrum's sprint-struktur.  
- [[Extreme Programming|XP]]: Lean fokus på enkelhed + XP's tekniske praksisser (fx TDD).  