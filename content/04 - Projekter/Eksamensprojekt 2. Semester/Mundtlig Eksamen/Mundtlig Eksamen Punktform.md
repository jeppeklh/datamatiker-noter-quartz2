
## **Mulige spørgsmål fra censor/vejleder**
#### Forretningsmodeller 
##### **Hvorfor kun BPMN og ikke BMC/business case?** 

- BPMN var tilstrækkeligt for vores projekt, da det fokuserede på at optimere en eksisterende proces frem for at skabe en ny forretningsmodel. 
- BPMN gav en detaljeret forståelse af workflowet i ferieplanlægningen, hvilket hjalp os med at identificere kravene. 

Fravalg af BMC/business case: 
- Vi havde en klar opgavestilling fra virksomheden, og projektets fokus var teknisk levering frem for strategisk udvikling. 
- En business case kunne have været relevant, hvis vi skulle overbevise virksomheden om værdien af løsningen. 

##### **Hvordan argumenterer I for projektets værdi?** 

- Tidsbesparelse: Fra uger til sekunder. 
- Retfærdighed: Automatisk fordeling mindsker fejl. 
- Brugervenlighed: Let at anvende for ledere. 


##### **Hvorfor vi fravalgte use case-diagrammer:**

1. **Kompleksiteten i projektet:**
    
    - Vores projekt havde relativt simple interaktioner med få aktører (medarbejder, leder og system). De vigtigste funktionaliteter – såsom indtastning af ferieønsker og beregning af ferieplanen – blev allerede tydeligt præsenteret i BPM’en. Et use case-diagram ville sandsynligvis ikke tilføje væsentlig ny værdi.
2. **Formålet med modellen:**
    
    - Vi prioriterede at illustrere **processernes flow** og de beslutninger, der træffes, fremfor at specificere systemfunktionaliteter. BPM’en opfylder dette formål, mens et use case-diagram er mere egnet til at kommunikere krav til softwaredesign eller testplanlægning.
3. **Publikum for rapporten:**
    
    - Rapportens målgruppe er primært ledere og interessenter uden teknisk baggrund. BPM’er er mere intuitive og letforståelige end use case-diagrammer, som kræver forståelse for UML-symbologi og systemkrav.

---

##### **Hvordan use case-diagrammet kunne have bidraget:** 

Hvis vi havde inkluderet et use case-diagram, kunne det have været nyttigt til at:
- Give en tydelig oversigt over, **hvilke funktionaliteter systemet tilbyder** (f.eks. "Indtast ferieønsker", "Godkend ferieplan").
- Vise relationerne mellem aktører (f.eks. medarbejdere og ledere) og systemets funktioner.
- Understøtte en kravspecifikation for udviklere ved at beskrive systemets grænser og primære funktioner.

#### Generelt om systemet 
---
##### **Hvordan håndterer jeres system transactions?** 

Hvorfor i C#: 
- Fleksibilitet: Transactions i C# giver mulighed for at kombinere flere databaseoperationer med logik i applikationen. 
- Debugging: Lettere at fejlsøge i koden end direkte i SQL. 

Hvordan det fungerer i projektet: 
- TransactionScope bruges til at indkapsle flere operationer som én transaction, fx: 
- Tilføjelse af ferieønske. 
- Opdatering af ferieplaner. 

Begrænsninger: 
- Håndteringen i applikationen kræver ekstra omhu for at sikre ikke at starte nye TransactionsScopes, hvis der allerede er et startet. 

##### **Hvordan sikrer jeres system datakonsistens?** 

1. Validering i applikationen: 
	- F.eks. tjekker algoritmen, om bemanding og kompetencer overholdes før allokering. 
2. Constraints i databasen: 
	- Primær- og fremmednøgler sikrer, at relationer mellem tabeller (fx Employee og VacationRequest) forbliver intakte. 
3. Transactions: 
	- Sikrer, at ændringer enten gennemføres eller rulles tilbage. 

Eksempel: 
- Hvis et ferieønske slettes, men tilhørende sletninger i ønskets ferieperioder fejler, rulles det hele tilbage. 

##### **Hvordan fungerer jeres integration mellem frontend og backend?** 

Dataflowet: 
1. Frontend (WPF UI): 
	- Brugeren interagerer med UI’et, f.eks. ved at indtaste ferieønsker. 
2. Backend: 
	- Data sendes fra UI til applikationslaget, hvor logikken behandles (f.eks. validering og ferieallokering). 
3. Database: 
	- Backend opdaterer databasen via repository-klasser. 

Fordele: 
- Lagdelt arkitektur sikrer separation af ansvar. 
- Let at udskifte eller opdatere enkelte lag uden at påvirke hele systemet. 

#### Sikkerhed og datahåndtering 
---
##### **Hvordan håndterer jeres system sikkerhed?** 

Sikkerhedsforanstaltninger: 
1. Rollebaseret adgang: 
	- Kun ledere kan oprette og slette ferieønsker for andre medarbejdere. 
2. Adgangskontrol: 
	- Medarbejdere kan kun se og ændre deres egne data. 

Manglende sikkerhed: 
- Ingen kryptering af følsomme data som adgangskoder. 

Fremtidige forbedringer: 
- Hashing af adgangskoder. 
- Kryptering af sensitive data. 

##### **Overvejelser om GDPR?** 

- GDPR ikke håndteret pga. klare instrukser fra Alfa Laval. 
- Foreslåede GDPR-tiltag: 
	- Kryptering af data. 
	- Sletning/anonymisering ved brugerens anmodning. 
	- Indhentning af samtykke. 


#### Testning og kvalitetssikring 
---
##### **Hvorfor var testdækningen begrænset?** 

- Vi forsøgte tidligt at lave tests på databaseniveau, men valgte at fjerne dem igen. 
- Årsag: Tests ændrede data i databasen, og vi håndterede dette ved at slette oprettede entries i samme test, hvilket gjorde dem komplekse og tidskrævende. 
- Vi var usikre på best practice, og det skabte yderligere udfordringer. 

Manglende mock-database: 
- En mock-database kunne have hjulpet med at teste uden at påvirke produktionsdata, men det var uden for pensum og krævede tid og viden, vi ikke havde på det tidspunkt. 

##### **Hvordan ville I strukturere tests fremadrettet?** 

Forslag til forbedringer: 
1. En klar teststrategi: 
	- Udarbejd en testplan tidligt i projektet, der dækker algoritmen, UI’et og integrationen mellem lagene. 
2. Brug af mock-databaser: 
	- Simuler databasen for at teste CRUD-operationer uden at påvirke rigtige data. 
3. Automatiserede tests: 
	- Implementer unit tests for: 
	- Algoritmen (sikring af korrekt ferieallokering, edge cases). 
	- UI-logik (validering af brugerinput). 
4. Integrationstests: 
	- Test hele forløb fra input i UI til databaseændringer og tilbage. 

Eksempel: 
- En mock-database kunne bruges til at teste ferieønsker: 
- Opret ferieønske → Valider data → Bekræft, at data blev gemt korrekt i databasen. 

#### Favalgte teknologier og metoder 
---
##### **Hvorfor ingen nedarvning?** 

- Fokus på opfyldelse af specifikke krav, hvor nedarvning ikke var nødvendig. 
- Nedarvning blev ikke brugt i det oprindelige design, da de fleste klasser havde separate ansvarsområder. 
- Dog kunne det være anvendt: 
	- Employee som baseklasse: 
    - Subklasser som RegularEmployee og Manager kunne specificere roller og adgange. 

- Fordele ved nedarvning: 
    - Reducerer kode-redundans. 
    - Gør systemet lettere at udvide med nye roller. 
    

##### **Hvordan kunne threads/processer forbedre systemet?** 

Nuværende situation: 
- Algoritmen eksekveres hurtigt (under 1 sekund) og programmet håndterer kun én bruger ad gangen, så der var ikke behov for threads. 

Fordele ved threads i fremtiden: 
1. Håndtering af samtidige brugere: 
	- Flere brugere kunne oprette ferieønsker eller generere ferieplaner på samme tid. 
	- Threads ville udnytte flere CPU-kerner, hvilket kunne forbedre performance. 
2. Asynkron eksekvering: 
	- Beregninger for ferieplanlægning kunne køre i baggrunden, så brugeren ikke skal vente på resultatet. 

Eksempel: 
- Hvis systemet blev udvidet til flere afdelinger, kunne ferieplanlægning for hver afdeling køre på separate threads. 

##### **Hvorfor transaktioner fremfor triggers?** 

Fordele ved transaktioner i applikationen (C#): 
1. Fleksibilitet: 
	- Transaktionslogik kan justeres og tilpasses direkte i koden uden at ændre SQL. 
2. Debugging: 
	- Lettere at fejlsøge applikationslogik i C# end i triggers, som kan være svære at spore. 

Ulemper ved triggers: 
1. Kan føre til uforudsigelige kædereaktioner, især hvis flere triggers påvirker hinanden. 
2. Mindre kontrol over, hvornår logikken udføres. 

Eksempel fra projektet: 
- Vi håndterede ferieønsker i C# ved at indkapsle flere databaseoperationer i én transaction. Dette gjorde det lettere at sikre, at kun fuldførte operationer blev gemt. 

#### Projektets begrænsninger og fremtidige udvikling 
---
##### **Hvad ville I ændre med mere tid?** 

Mulige forbedringer: 
1. Optimering af algoritmen: 
	- Reducering af kompleksiteten for hurtigere eksekvering. 
	- Forbedring af fairness ved at analysere edge cases mere detaljeret. 
2. Brugeroplevelse: 
	- Tilføjelse af mere brugervenlige funktioner: 
	- Mulighed for at slette kompetencer og ferietyper (Selv hvis der er ferieønsker tilknyttet). 
	- Bedre visualisering af ferieplaner. 
3. Sikkerhed: 
	- Implementér kryptering af følsomme data som adgangskoder. 
4. Testdækning: 
	- Brug af mock-databaser og automatiserede tests til at sikre kvalitet.


#### Problematikken med use case 2
---
##### **Hvorfor var Use-Case 2 særligt problematisk?**

- **Kompleksitet:** Use-Case 2 dækker tre konceptuelle klasser:
    - `Lagermedarbejder`
    - `Kompetence`
    - `Ferieønske`  
    Disse klasser udgør størstedelen af modellaget i vores program og krævede hver især betydeligt arbejde.
- **Scope:** Use-casen var for bred til at passe ind i ét sprint og burde være opdelt i tre separate use-cases eller sprints.
- **Læring:** Vi indså undervejs, at opdeling ville have gjort arbejdsprocessen mere overskuelig og mindsket overlap mellem klasserne.

##### **Hvordan kunne Use-Case 2 have været opdelt for at mindske problemerne?**
- Opdelingen kunne have været baseret på de tre konceptuelle klasser:
    1. **Lagermedarbejdere:** Fokus på at oprette og vedligeholde medarbejderdata.
    2. **Kompetencer:** Sikre, at hver medarbejder har korrekt tilknyttede kompetencer.
    3. **Ferieønsker:** Håndtering af medarbejdernes ønsker og validering af input.
- **Fordel ved opdeling:**
    - Mindre afhængighed mellem klasserne i udviklingsprocessen.
    - Mulighed for hurtigere levering af delmål, hvilket kunne give hurtig feedback fra interessenter.

##### **Hvordan påvirkede ændringer i kravene fra interessenter Use-Case 2?**

- **Sen ændring:** Alfa Laval ønskede en funktion, hvor lagermedarbejdere selv kunne indtaste ferieønsker, frem for at dette blev håndteret af lederen.
- **Effekt:**
    - Ændringen blev tilføjet i systemet, men ikke repræsenteret i use-casen eller modellerne pga. tidsmangel.
    - Vi vurderede, at det ikke påvirkede de centrale stamdata eller systemets kernefunktioner, hvorfor vi ikke opdaterede dokumentationen.

##### **Hvordan kan erfaringerne fra Use-Case 2 bruges fremadrettet?**

- **Bedre opdeling:**
    - Fremover ville vi sikre, at komplekse use-cases opdeles i mindre, selvstændige use-cases, hver med et klart scope og mål.
- **Iterativ dokumentation:**
    - Ændringer i kravene ville blive reflekteret i modeller og use-cases, så dokumentationen altid er opdateret.
- **Tættere samarbejde:**
    - Tættere dialog med interessenter kunne have hjulpet med at forudse ændringer og planlægge for dem tidligere i processen.

##### **Hvilken værdi havde modellerne ud over dokumentation?**

- Modellerne fungerede som et kommunikationsværktøj:
    - De hjalp med at sikre, at alle i gruppen havde samme forståelse af, hvordan systemet skulle designes.
    - De gav overblik over relationer mellem klasser, som hjalp os med at undgå designfejl.

#### DCD
---
##### **Hvilken værdi havde DCD’et, selvom I ikke brugte det konsekvent?**

- DCD’et var afgørende for at skabe et overblik i begyndelsen af projektet.
- Det fungerede som et fundament for vores designvalg og sikrede sporbarhed mellem domænemodellen og implementeringen.
- Selvom det ikke blev brugt løbende, var det en vigtig dokumentation for at vise systemets struktur og relationer.

##### **Hvad er de største fordele og ulemper ved jeres tilgang til DCD’et?**

**Fordele:**
1. Hjælp til kommunikation i de tidlige faser af projektet.
2. Skabte en bro mellem domænemodellen og implementeringen.
3. Endelig version giver et klart overblik over systemets klasser og relationer.

**Ulemper:**
1. Den iterative tilgang gjorde det svært at holde diagrammet opdateret.
2. Kompleksiteten steg markant, hvilket reducerede dets læselighed.
3. Diagrammet blev nedprioriteret senere i projektet, hvilket kunne skabe huller i kommunikationen.