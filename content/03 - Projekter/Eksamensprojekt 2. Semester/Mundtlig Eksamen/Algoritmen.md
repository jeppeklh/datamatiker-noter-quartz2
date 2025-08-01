### **Overordnet funktionalitet**

Algoritmen har til formål at planlægge medarbejdernes ferie på en måde, der opfylder virksomhedens minimumsbemandingskrav og sikrer, at kompetencekravene opretholdes. Den tager input som:

- En liste af arbejdsdage og minimumsbemandingskrav pr. dag.
- En liste af medarbejdere med deres kompetencer og ferieønsker.
- En specifik ferietype.

Algoritmen forsøger at allokere medarbejdernes ferieønsker så retfærdigt som muligt.

---

### **Hvad du bør kunne forklare**

#### **Algoritmen: Input, output og flow**

1. **Input**:
    
    - Liste over arbejdsdage og minimumsbemanding pr. dag.
    - Medarbejderliste med kompetencer og ferieønsker.
    - Specifik ferietype.
2. **Output**:
    
    - CSV-fil, der viser ferieplanen for hver medarbejder.
    - Status på opfyldelse af bemandings- og kompetencekrav.
3. **Flow**:
    
    - Validering → Transformation → Sortering → Allokering → Generering af output.

---

### **Mulige spørgsmål og svar**

#### **1. Hvordan sikrer algoritmen fairness i allokeringen?**

- Medarbejdere grupperes efter sidste års prioritet, og rækkefølgen inden for grupper randomiseres.
- Ferieønsker prioriteres i stigende rækkefølge, så medarbejdere med højere prioritet får førsteret.

#### **2. Hvordan håndterer algoritmen bemandings- og kompetencekrav?**

- Før hver ferieallokering tjekkes, om bemandingskravet og kompetencekrav kan opfyldes, hvis ønsket tildeles.
- Hvis nogle krav brydes, afvises ønsket.

#### **3. Hvorfor er bemandingskravet transformeret fra procent til en absolut værdi?**

- Transformationen gør det muligt at arbejde med faktiske tal (antal medarbejdere) fremfor procent, hvilket forenkler beregningerne.

#### **4. Hvordan kunne algoritmen forbedres?**

- **Performance**: Optimer kørslen ved at reducere gentagne opslag i lister.
- **UI-forbedringer**: Gør det nemmere for brugere at justere input (f.eks. dynamisk valg af kompetencekrav).

#### **5. Hvordan hænger flowchartet sammen med algoritmen?**

- Flowchartet repræsenterer hovedtrinene i algoritmen:
    - Sortering af medarbejdere.
    - Validering og allokering af ferie.
    - Opdatering af lister for bemanding/kompetence og generering af output.

---

### **Hvordan kan du lære det udenad?**

1. **Skab mentale billeder**:
    - Visualisér flowet fra input til output med flowchartet som reference.
2. **Lav flashcards**:
    - Fx:
        - Q: Hvad er input til algoritmen?  
            A: Liste over arbejdsdage, medarbejderliste, ferietype.
3. **Forklar det højt**:
    - Simuler eksamensspørgsmål med en ven eller alene.
4. **Tegn flowchartet**:
    - Tegn det flere gange og brug det til at forklare algoritmens logik.



---
---
### **Hovedmetoder i klassen**

Algoritmen har et klart flow, der drives af følgende metoder:

1. **`ValidateInputs`**
2. **`TransformInputs`**
3. **`SortEmployeesAndTransformToQueue`**
4. **`FlowController`**
5. **`TryToAllocateNextVacationRequest`**
6. **`CheckVacationRequestAgainstHardConstraints`**
7. **`GenerateSchedule`**

For hver metode beskrives, hvad den gør, hvordan den gør det, og hvordan den passer ind i det samlede flow.

---

### **1. `ValidateInputs`**

#### **Hvad gør metoden?**

- Tjekker, om de indleverede inputs er gyldige for algoritmen. Dette er en forudsætning for, at algoritmen overhovedet kan køre.
- **Output:** Returnerer `true`, hvis alle inputs er gyldige.

#### **Hvordan gør den det?**

- Indeholder en placeholder-implementering i koden, som mangler konkret valideringslogik.
- Eksempel på, hvad den kunne validere:
    - At der findes mindst én arbejdsdag.
    - At ferietypen har definerede krav (fx minimumsbemanding og kompetencer).

#### **Rolle i flowet**

- Sørger for, at algoritmen kun starter, hvis inputdata er korrekt struktureret.

---

### **2. `TransformInputs`**

#### **Hvad gør metoden?**

- Transformer inputlisterne til en form, der kan bruges direkte af algoritmen.
- **Output:** Opdaterede datastrukturer (`vacationtypeWorkDayList`, `unallocatedEmployeeList`).

#### **Hvordan gør den det?**

- **Transformerer arbejdsdage (`minWorkForceReq`):**
    
    - Gør minimumsbemandingskrav til absolutte tal i stedet for procent.
    - Matcher dage med specifikke kompetencekrav fra `VacationType.SkillRequirementList`.
- **Bygger listen over medarbejdere (`unallocatedEmployeeList`):**
    
    - Indsamler hver medarbejders ferieønsker og kompetencer.
    - Opdaterer deres prioritet baseret på sidste års ferieallokering.

#### **Rolle i flowet**

- Skaber grundlaget for, at algoritmen kan arbejde effektivt med bemandings- og kompetencekrav.
- Klargør medarbejderdata til sortering og køhåndtering.

#### **Datastrukturer der opdateres**

1. **`vacationtypeWorkDayList`**

- Indhold: En liste af dage med bemandings- og kompetencekrav.
- Form:
```csharp
(DateTime day, int workForceLimit, List<(string skillName, int requirement)> skillRequirementLimits)
```
- Formål: Indeholder kravene for hver dag og opdateres løbende for at sikre, at ingen krav brydes.


2. **`unallocatedEmployeeList`**

- Indhold: Medarbejdere med deres ferieønsker, kompetencer og sidste års prioritet.
- Form:
```csharp
(int employeeId, int? lastYearsPriority, List<(string skillName, bool trained)> skillSet, List<(int priority, List<DateTime> days)> vacationRequests)
```
	
- Formål: Bruges til at afgøre, hvilke medarbejdere der kan allokeres ferie.

---

### **3. `SortEmployeesAndTransformToQueue`**

#### **Hvad gør metoden?**

- Sorterer medarbejderne baseret på sidste års prioritet og gør dem klar til behandling i en kø.

#### **Hvordan gør den det?**

1. **Gruppér medarbejdere** efter sidste års prioritet (grupper med højere prioritet behandles først).
2. **Randomisér rækkefølgen** inden for hver prioritet for at sikre fairness.
3. **Sortér ferieønsker** for hver medarbejder i stigende rækkefølge efter prioritet.
4. **Læg medarbejdere i en kø** (`sortedUnallocatedEmployeesQueue`).

#### **Rolle i flowet**

- Skaber en fair og prioriteret kø af medarbejdere til behandling i algoritmens hovedlogik.

---

### **4. `FlowController`**

#### **Hvad gør metoden?**

- Hovedmetoden, der styrer allokeringen af ferie.
- **Output:** Opdaterer listerne over allokerede og ikke-allokerede medarbejdere.

#### **Hvordan gør den det?**

1. Henter en medarbejder fra køen.
2. Gennemgår medarbejderens ferieønsker i prioriteret rækkefølge.
3. Prøver at allokere hvert ønske via `TryToAllocateNextVacationRequest`.
4. Flytter medarbejderen til enten `allocatedEmployeeList` eller `failedToAllocateEmployeeList` baseret på resultatet.

#### **Rolle i flowet**

- Driver hele allokeringsprocessen og sikrer, at medarbejdere behandles korrekt i forhold til deres ønsker og systemets begrænsninger.

---

### **5. `TryToAllocateNextVacationRequest`**

#### **Hvad gør metoden?**

- Forsøger at opfylde en medarbejders ferieønske ved at kontrollere bemandings- og kompetencekrav.

#### **Hvordan gør den det?**

1. Tjekker ønsket mod hårde begrænsninger via `CheckVacationRequestAgainstHardConstraints`.
2. Hvis valideringen lykkes:
    - Opdaterer `vacationtypeWorkDayList` for hver dag i ønsket.
    - Reducerer bemandingskrav og kompetencekrav med 1 for hver dag.

#### **Rolle i flowet**

- Kontrollerer og udfører allokeringen for individuelle ferieønsker.

---

### **6. `CheckVacationRequestAgainstHardConstraints`**

#### **Hvad gør metoden?**

- Validerer, om en medarbejders ferieønske kan opfyldes uden at bryde bemandings- eller kompetencekrav.

#### **Hvordan gør den det?**

1. Gennemgår hver dag i ønsket.
2. Kontrollerer, om bemandingskravet kan opretholdes (antal medarbejdere må ikke falde under grænsen).
3. Kontrollerer, om kompetencekravet kan opretholdes (antal medarbejdere med specifikke kompetencer må ikke falde under grænsen).

#### **Rolle i flowet**

- Sikrer, at allokering kun sker, hvis alle krav overholdes.

---

### **7. `GenerateSchedule`**

#### **Hvad gør metoden?**

- Genererer en CSV-fil, der opsummerer ferieplanen og status for bemandings-/kompetencekrav.

#### **Hvordan gør den det?**

1. Opretter rækker for medarbejdere med deres ferieplaner.
2. Tilføjer status for resterende bemandings- og kompetencekrav pr. dag.
3. Skriver uallokerede medarbejdere i bunden af filen.

#### **Rolle i flowet**

- Leverer algoritmens output i et letlæseligt format til brugeren.

---

### **Datastrukturer og deres rolle**

1. **`vacationtypeWorkDayList`**: Holder styr på, hvilke dage der stadig opfylder bemandings- og kompetencekrav.
2. **`unallocatedEmployeeList` → `sortedUnallocatedEmployeesQueue`**: Flytter medarbejdere fra en generel liste til en prioriteret kø.
3. **`allocatedEmployeeList` / `failedToAllocateEmployeeList`**: Adskiller succesfulde og mislykkede allokeringer.


---
---
### **Nøglefunktioner i algoritmen**

### **Tilføjet logik fra ViewModel (AlgorithmVVM)**

1. **Dataklargøring**:
    
    - Henter medarbejdere fra en database (via repositories) og sorterer dem i lister baseret på roller (f.eks. studerende vs. fuldtidsansatte).
2. **Brugerinteraktion**:
    
    - Bruger kan vælge ferietype, indstille minimumsbemanding og markere daghold/nathold.
    - Tilføjer/tilpasser medarbejdere baseret på deres status.
3. **Kørsel af algoritmen**:
    
    - Tjekker, om der er nok data (ferietype, bemanding osv.).
    - Initialiserer og kører algoritmen med brugerspecificerede input.

---
