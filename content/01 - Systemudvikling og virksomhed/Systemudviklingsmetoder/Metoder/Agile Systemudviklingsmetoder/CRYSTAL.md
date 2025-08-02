
>[!tldr] Definition
> **Crystal** er en familie af [[Agile|agile]] metoder designet til at tilpasse sig projektets størrelse og kompleksitet. Hver metode i Crystal-familien er navngivet efter en farve, der angiver teamstørrelse, og kombineres med en "kritikalitetsniveau" (risikoen ved fejl). Crystal fokuserer på fleksibilitet, kommunikation og minimal proces-overhead.
> 
> [[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=531&selection=71,0,71,6|p.495]]

---

## Kerneprincipper
Alle Crystal-metoder deler disse 7 kerneegenskaber:
1. **Hyppige iterationer**: Korte udviklingscyklusser med løbende leverancer.
2. **Konstant feedback**: Regelmæssige møder med team og kunder for justeringer.
3. **Nær kommunikation**: Teamet arbejder fysisk tæt (ideelt samme rum).
4. **Sikkerhed**: 
   - Tryghed for teammedlemmer til at udtrykke meninger.
   - Projektsikkerhed (deadlines/budget).
   - Kritikalitetsniveau (fx liv vs. komfort).
5. **Fokus**: Mindst 2 timers uafbrudt arbejde dagligt. Klare prioriteter.
6. **Adgang til ekspertbrugere**: Eksperter skal være tilgængelige for spørgsmål.
7. **Teststøtte**: Automatiserede tests og versionskontrol.

---

## Crystal Matrix: Farver & Kritikalitet

| Teamstørrelse       | Komfort (C) | Økonomi (D/E) | Liv (L)       |
|----------------------|-------------|---------------|---------------|
| **Clear (1-6)**      | C6          | D6/E6         | L6            |
| **Yellow (7-20)**    | C20         | D20/E20       | L20           |
| **Orange (21-40)**   | C40         | D40/E40       | L40           |
| **Red (41-80)**      | C80         | D80/E80       | L80           |
| *Større projekter*   | ...         | ...           | ...           |
>[!example] Eksempel
Et projekt med 35 personer og livskritikalitet kaldes "L40 (Orange)".

---

## Crystal-metoder

### Crystal Clear (1-6 personer)
- **Roller**:
	- Sponsor (godkender produktet)
	- Senior designer (teknisk leder)
	- Programmører (udvikler kode)
- **Praksis**:
	- Uformel kommunikation. Ingen detaljerede kravdokumenter.
	- Levering hver 2-3 måned med kundefeedback.
	- Minimal proces – fokus på kode og løbende justeringer.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=534&selection=19,0,19,13|p.498]]
### Crystal Yellow (7-20 personer)
- **Tilføjelser**:
	- Opdeling i underhold med hvert sit ansvarsområde.
	- Missionerklæring for fælles vision.
	- Månedlige, tidsbegrænsede iterationer.
- **Roller**: Teamledere, forretningsanalytiker (valgfri).
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=534&selection=60,0,60,14|p.498]]
### Crystal Orange (21-40 personer)
- **Formalisering**:
	- Kravdokumentation og accepttests.
	- Projektleder til opgavesporing.
	- Arkitekt til systemdesign.
- **Roller**:
	 - Forretningsanalytiker
	- Projektleder
	- Teknisk forfatter
	- Testere
- **Praksis**:
	- Formel release-planlægning.
	- Kodegennemgange og risikostyring.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=535&selection=60,0,60,14|p.499]]

---

## Hvorfor vælge Crystal?
- **Fleksibilitet**: Tilpasses til projektets størrelse og risiko.
- **Kommunikation før dokumentation**: Mindre bureaukrati i små teams.
- **Skalerbarhed**: Klare retningslinjer for store projekter.

---

## Begrænsninger
- **Store projekter**: Kræver stram struktur (kan føles byrdefuldt).
- **Uklare krav**: Uformel tilgang risikerer scope creep i komplekse projekter.
- **Manglende standard**: Mindre udbredt end [[SCRUM]]/[[Extreme Programming|XP]], færre værktøjer.
