---
aliases:
  - DSDM
---

>[!tldr] Definition
> **DSDM** (Dynamic Systems Development Method) er en [[Agile]]-ramme. Metoden kombinerer forretningsdisciplin med fleksibel udvikling og er særlig egnet til komplekse projekter med høje krav til leverancehastighed. DSDM lægger vægt på **samarbejde**, **hyppig levering** og **forretningsmæssig værdi**.
>
> [[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=544&selection=17,0,17,34|p.508]]

---

## Faser i DSDM
### 1. Pre-project
- **Formål**: Forberedelse af projektet.  
- **Aktiviteter**:  
	- Identifikation af mulige projekter.  
	- Sikring af ledelsesstøtte og finansiering.  

### 2. Project Life Cycle (Hovedudvikling)
- **Study**:  
  - *Feasibility Study*: Vurderer projektets tekniske muligheder.  
  - *Business Study*: Afgør projektets forretningsmæssige værdi (brug af **MOSCOW-metoden** til prioritering).  

- **Model Functionality**:  
	- Udvikling af prototyper og funktionelle modeller gennem gentagne cyklusser:  
		- Identificer prototype → Planlæg → Byg → Gennemgå.  

- **Design and Build**:  
	- Integration af modeller til en samlet prototype.  
	- Gentagne iterationer med brugerfeedback.  

- **Implementation**:  
	- Udrulning, brugeruddannelse og evaluering af resultater.  

### 3. Post-project
- Vedligeholdelse, fejlrettelser og opdateringer.

[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=544&selection=39,0,39,11|p.508]]
## Kerneprincipper
---
1. **Aktiv brugerinvolvering**: Brugere deltager kontinuerligt i design og feedback.  
2. **Hyppig levering**: Funktionel software leveres hurtigt (fokus på **80/20-reglen** – 80% af værdien i 20% af tiden).  
3. **Iterativ og inkrementel**: Løsningen udvikles trinvis med løbende justeringer.  
4. **Reversible ændringer**: Alle ændringer skal kunne rulles tilbage (versionskontrol).  
5. **Konstant testning**: Test gennem hele livscyklussen for høj kvalitet.  
6. **Samarbejde**: Tæt dialog mellem udviklere, brugere og ledelse.  
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=546&selection=8,0,8,15|p.510]]

---

## Roller
### Primære Roller
| **Rolle**             | **Ansvar**                                                                 |
|------------------------|----------------------------------------------------------------------------|
| **Executive Sponsor**  | Sikrer ressourcer og fjerner forhindringer.                                |
| **Ambassador User**    | Brobygger mellem brugere og udviklere.                                     |
| **Technical Coordinator** | Ansvarlig for systemarkitektur og teknisk kvalitet.                    |
| **Project Manager**    | Styring af tidsplaner og budget.                                           |

### Sekundære Roller (udvalgte)
- **Business Visionary**: Klar vision for projektets forretningsmål.  
- **DSDM Coach**: Vejleder teamet i metodens brug.  
- **Quality Manager**: Sikrer kvalitet gennem tests og reviews.  
- **Workshop Facilitator**: Ledelse af workshops til kravindsamling.  

[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=547&selection=6,0,6,10|p.511]]

---

## Fordele vs. Udfordringer

| **Fordele**                          | **Udfordringer**                          |
|---------------------------------------|--------------------------------------------|
| Klare faser giver struktur            | Kompleksitet kan overvælde små projekter   |
| Stærk forretningsfokus                | Kræver erfaren facilitering af workshops   |
| Fleksibilitet gennem prototyper       | Mange roller kan skabe uklarhed            |
| Egnet til regulerede brancher         | Dokumentationsbyrde i tidlige faser       |

---

## Hvorfor vælge DSDM?
- **Komplekse projekter**: Kombinerer agility med forretningsstyring.  
- **Hurtig værdilevering**: Fokus på kernefunktioner først (80/20).  
- **Transparent proces**: Tydelige faser og ansvarsroller.  

