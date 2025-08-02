---
aliases:
  - XP
---

>[!tldr] Definition
> **Extreme Programming (XP)** er en [[Agile]]-metode, der tager almindelige udviklingspraksisser til det ekstreme for at øge kvalitet og hastighed. XP fokuserer på hyppig feedback, kontinuerlig forbedring og tæt samarbejde mellem udviklere og kunder.
>
> [[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=514&selection=35,0,35,2|p.478]]

---

## XP Roller
- **Kunde**: Definerer krav, tester løsninger og giver løbende feedback.  
- **Tracker**: Måler teamets fremskridt og identificerer risici.  
- **Udvikler**: Designer arkitektur og skriver kode (ofte i par).  
- **Coach**: Hjælper teamet med at følge XP-principper.  
- **Tester**: Sikrer, at koden opfylder krav via accepttests.  
- **Administrator**: Opsætter og vedligeholder tekniske værktøjer.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=515&selection=0,2,50,8|p.479]]

---

## Kerneværdier
1. **Kommunikation**: Tæt dialog mellem team og kunde.  
2. **Enkelhed**: Minimalt design, der løser dagens problem (*YAGNI*: "You Ain’t Gonna Need It").  
3. **Feedback**: Kontinuerlig testning og kundeinput.  
4. **Mod**: Refaktorér kode, nødvendigt – selv hvis det kræver store ændringer.  
5. **Respekt**: Teamet arbejder sammen med gensidig tillid.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=516&selection=51,0,51,9|p.480]]

---

## Nøglepraksisser
### 1. Pair Programming
- To udviklere arbejder sammen på én computer:  
	- **Driver**: Skriver kode og forklarer tanker.  
	- **Navigator**: Reviewer kode i realtid og foreslår forbedringer.  
- **Fordele**: Færre fejl, bedre viden-deling, højere kvalitet.

### 2. Kundesamarbejde
- En **on-site kunde** er tilgængelig dagligt for at besvare spørgsmål og prioritere opgaver.

### 3. Iterativ Planlægning (Planning Game)
- **Release-planlægning**: Kunden vælger vigtige features (user stories), teamet estimerer tid.  
- **Iterationsplanlægning**: Opdeler features i 1-3 ugers iterationer med daglige opgaver.

### 4. Hyppige Små Releases
- Lever **nye versioner hver 1-4 uger** for tidlig feedback og mindre risiko.

### 5. Enkel Design
- Start med den *mest simple løsning*. Kun tilføj kompleksitet, når behvis dokumenteret nødvendigt.

### 6. Kontinuerlig Test
- Automatiserede tests køres **dagligt/natligt**.  
- Nye fejl føjes til testsuiten for at undgå gentagelser.

### 7. Refaktorering
- Omstrukturer kode løbende for at holde den ren og vedligeholdelig – *uden at ændre funktionalitet*.

### 8. Kollektiv Kodeejerskab
- Alle kan redigere enhver kode. Ingen "gatekeepers" – men brug versionskontrol (fx Git).

### 9. Kodningsstandarder
- Ensartet kode gør det lettere at læse og redigere på tværs af teamet.

### 10. Bæredygtigt Tempo
- **Max 40 timer/uge** for at undgå udbrændthed. Ingen overarbejde!

### 11. Test-Drevet Udvikling (TDD)
- **TDD**: Skriv test → skriv minimal kode → refaktorér.  
- **Test-First**: Skriv *alle tests* før kode. Sikrer fokus på korrekt funktionalitet.

[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=517&selection=22,0,22,12|p.481]]

---

## Fordele vs. Udfordringer

| **Fordele**                          | **Udfordringer**                          |
|---------------------------------------|--------------------------------------------|
| Høj kodekvalitet gennem konstant review | Kræver erfarne og modne udviklere         |
| Tidlig feedback fra kunde             | On-site kunde kan være svær at sikre      |
| Fleksibel til ændrede krav             | Parprogrammering kan føles ubehageligt    |
| Mindre tekniske gæld                  | Kortere deadlines kan føles pressede      |

---

## XP vs. Traditonelle Metoder
- **Mere feedback**: Kode testes og leveres løbende.  
- **Mindre dokumentation**: Fokus på funktionel kode fremfor detaljerede specs.  
- **Større teamansvar**: Kollektiv ejerskab kræver kommunikation og tillid.