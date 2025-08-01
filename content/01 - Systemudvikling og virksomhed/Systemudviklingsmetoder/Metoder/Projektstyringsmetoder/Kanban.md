>[!tldr] Definition
**Kanban** (japansk for "skilt" eller "tavle") er en **agile-metode**, der fokuserer på visuel styring af arbejdsflow og kontinuerlig forbedring. Oprindeligt brugt i produktion til lagerstyring, er Kanban i dag populær i softwareudvikling for at øge effektiviteten og reducere spild.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=548&selection=76,0,76,6|p.512]]

---

## Kerneprincipper
---
1. **Start med nuværende praksis**: Tilpas Kanban til eksisterende processer – ingen radikal omvæltning.  
2. **Gradvise ændringer**: Indfør små, inkrementelle forbedringer for at mindske modstand.  
3. **Respektér eksisterende roller**: Bevar teamets struktur og ansvarsområder.  
4. **Fremme lederskab hos alle**: Opfordrer til initiativ og ejerskab hos alle teammedlemmer.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=549&selection=19,0,19,17|p.513]]

## Praksisser
---
- **Visualisér workflow**: Brug et Kanban-board til at vise opgaver og deres status.  
- **Begræns igangværende arbejde (WIP)**: Undgå overbelastning ved at sætte max-grænser for antal opgaver i hver fase.  
- **Forbedr flow**: Prioriter opgaver løbende og "træk" nye opgaver, når kapacitet frigøres.  
- **Mål og optimer**: Brug data (fx gennemløbstid) til at identificere flaskehalse.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=549&selection=59,0,59,16|p.513]]

## Kanban-board
---
Et typisk board indeholder kolonner som:  
$Backlog → Ready → Coding → Testing → Done$

>[!example] Eksempel
| Backlog | Design (WIP) | Coding (WIP) | Testing (WIP) | Done |
|---------|--------------|--------------|---------------|------|
| Task 5  | Task 3       | Task 1       | Task 2        | Task4| 
>
>- **WIP-limiter**: Fx max 3 opgaver i "Coding" for at undgå overbelastning.  
>- **Kort**: Viser opgave-ID, beskrivelse, ansvarlig og deadline.

[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=550&selection=39,0,39,12|p.514]]
## Fordele vs. Udfordringer
---

| **Fordele**                          | **Udfordringer**                          |
|---------------------------------------|--------------------------------------------|
| Fleksibilitet til ændringer           | Kræver disciplin for at overholde WIP-grænser |
| Reduceret spild og multitasking       | Uklarhed ved for komplekse boards          |
| Forbedret gennemsigtighed             | Manglende deadlines kan udfordre planlægning |
| Egnet til vedligeholdelsesprojekter   | Svært at skaleres til meget store teams     |



## Hvornår bruge Kanban?
---
- **Support/vedligeholdelse**: Løbende rettelser og små opdateringer.  
- **Team med varieret arbejdsbyrde**: Prioritering sker dynamisk.  
- **Projekter med hyppige ændringer**: Hurtig tilpasning til nye krav.

## Resourser
---
- [Kanban LinkedIn Learning](https://www.linkedin.com/learning/stay-lean-with-kanban/pitfalls-of-kanban?u=57075649)