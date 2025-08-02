
>[!tldr] Definition
> **Scrum** er en [[Agile]]-metode, der strukturerer udvikling i korte iterationer ("sprints") med fokus på selvorganiserende teams og kontinuerlig forbedring. 
>
> [[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=524&selection=32,0,32,5|p.488]]

---

## Scrum-roller

| **Rolle**         | **Ansvar**                                                                 |
|--------------------|----------------------------------------------------------------------------|
| **Product Owner**  | - Repræsenterer kunden/brugere<br>- Prioriterer opgaver i *product backlog*<br>- Godkender leverancer |
| **Scrum Master**   | - Fjerner forhindringer for teamet<br>- Sikrer overholdelse af Scrum-principper<br>- Faciliteter møder |
| **Teammedlemmer**  | - Selvorganiserende udviklere<br>- Arbejder tværfagligt på alle opgaver i sprintet |

[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=525&selection=14,0,14,11|p.489]]

---

## Scrum-sprints
- **Varighed**: Typisk 2-4 uger (30 dage i klassisk Scrum).  
- **Output**: *Potentially Shippable Increment (PSI)* – testet, funktionel software klar til release.  
- **Faser**:  
  1. **Planlægning**: Vælg opgaver fra *product backlog* til *sprint backlog*.  
  2. **Udførelse**: Daglige *standups* og kodning.  
  3. **Review**: Demo af PSI til Product Owner.  
  4. **Retrospective**: Evaluering af proces/forbedringer.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=526&selection=13,0,13,13|p.490]]

---

## Nøglemøder
1. **Sprint Planning**  
	- *Hvornår*: Før hvert sprint.  
	- *Formål*: Vælg og opdel opgaver fra product backlog til sprint backlog.  

2. **Daily Scrum (Standup)**  
	- *Hvornår*: Dagligt (max 15 min.).  
	- *Spørgsmål*:  
	     - Hvad gjorde jeg i går?  
	     - Hvad laver jeg i dag?  
	     - Hvad blokerer mig?  

3. **Sprint Review**  
   - *Hvornår*: Efter hvert sprint.  
   - *Formål*: Demo af PSI og justering af product backlog.  

4. **Retrospective**  
   - *Hvornår*: Efter review.  
   - *Formål*: Refleksion over "hvad gik godt/dårligt?" og procesoptimering.

---

## Estimeringsteknikker
### Planning Poker
- **Hvordan**:  
	- Teamet bruger kort med Fibonacci-tal (1, 2, 3, 5, 8, 13...) til at estimere opgavers kompleksitet.  
	- Kort vendes samtidigt for at undgå bias.  
- **Formål**: Skab konsensus om opgavers *story points* (relativ størrelse).
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=527&selection=42,0,42,14|p.491]]
### Burndown Charts
- **Hvad**: Graf der viser **ubegyndt arbejde** over tid.  
- **Brug**:  
	- *Sprint burndown*: Sporer fremskridt i nuværende sprint.  
	- *Product burndown*: Viser samlet resterende arbejde for projektet.  
![[Repo/05 - Images/Systemudvikling og virksomheden/BurndownChart.png]]
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=528&selection=48,0,48,8|p.492]]

---

## Velocity
- **Definition**: Mængden af *story points* et team gennemfører pr. sprint.  
- **Brug**: Forudsig fremtidig produktivitet (fx: Hvis velocity = 20, kan 100 SP forventes afsluttet på 5 sprints).  
- **Variationer**: Påvirkes af teams størrelse, erfaring og sprint-længde.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=530&selection=8,0,8,8|p.494]]

---

## Fordele vs. Udfordringer

| **Fordele**                          | **Udfordringer**                          |
|---------------------------------------|--------------------------------------------|
| Klare deadlines og målbare fremskridt | Kræver disciplin til daglige standups      |
| Fleksibel til ændrede prioriteringer  | Product Owner skal være tilgængelig        |
| Transparent proces via boards/charts  | Svært at estimere story points præcist     |

---

## Scrum i Praksis
- **Kombineres ofte** med tekniske metoder som [[Extreme Programming|XP]] (test-drevet udvikling, pair programming).  
- **Succesfaktorer**:  
	- Engageret Product Owner  
	- Selvorganiserende team med tværfaglige kompetencer  
	- Konsekvent brug af Scrum-ritualer (møder, charts)

---

## Resourcer
- [SCRUM LinkedIn Kursus]()