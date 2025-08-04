#flashcards/Eksamensprojekt/Programmering
Hvilken værdi havde DCD’et, selvom I ikke brugte det konsekvent?
?
- DCD’et var afgørende for at skabe et overblik i begyndelsen af projektet.
- Det fungerede som et fundament for vores designvalg og sikrede sporbarhed mellem domænemodellen og implementeringen.
- Selvom det ikke blev brugt løbende, var det en vigtig dokumentation for at vise systemets struktur og relationer.

Hvad er de største fordele og ulemper ved jeres tilgang til DCD’et?
?
**Fordele:**
1. Hjælp til kommunikation i de tidlige faser af projektet.
2. Skabte en bro mellem domænemodellen og implementeringen.
3. Endelig version giver et klart overblik over systemets klasser og relationer.
**Ulemper:**
1. Den iterative tilgang gjorde det svært at holde diagrammet opdateret.
2. Kompleksiteten steg markant, hvilket reducerede dets læselighed.
3. Diagrammet blev nedprioriteret senere i projektet, hvilket kunne skabe huller i kommunikationen.

Hvorfor ingen arv og polymorfi?
?
- Fokus på opfyldelse af specifikke krav, hvor arv ikke var nødvendig.
- Fremtidig iteration:
    - `Employee`-baseklasse med nedarvede klasser (`Manager`, `RegularEmployee`).


Hvordan kunne threads/processer forbedre systemet?
?
- Kunne håndtere flere samtidige brugere.
- Eksempler:
    - Baggrundsprocesser til ferieallokering.
    - Forbedret GUI, der kan forblive aktiv under beregninger.


Hvorfor transaktioner fremfor triggers?
?
- Triggers: Kan sikre datakonsistens, men skaber uforudsigelighed.
- Transaktioner:
    - Lettere debugging.
    - Mere fleksible i applikationslaget.


Hvordan sikrer I medarbejderdata?
?
- Ingen kryptering implementeret, men foreslåede løsninger:
    - **Hashing:** Beskytter passwords.
    - **Adgangskontrol:** Rollebaserede rettigheder (manager/medarbejder).


Hvorfor var testdækningen begrænset?
?
- Tidlige forsøg på database-tests fjernet (komplekse og usikkerhed om best practice).
- Ingen mock-database anvendt, hvilket kunne have hjulpet.


Hvordan ville I strukturere tests fremadrettet?
?
- **Unit tests:** Til algoritmer og UI-logik.
- **Integrationstests:** Sikre flow mellem lagene.
- **UI-tests:** Automatiserede tests af brugergrænsefladen.



#flashcards/Eksamensprojekt/Systemudvikling

Hvordan har kvalitetskriterier påvirket jeres systemudviklingsproces?
?
- **Svar:** Vi fokuserede på kvalitet ved at sikre sporbarhed gennem brugen af modeller som BPMN og objektmodeller, der sikrer sammenhæng mellem krav og implementering.
    - Eksempel: Fra en use case som _"Opret ferieønske"_ blev der designet en objektmodel med `VacationRequest`, der direkte påvirkede designet af databasen og koden.

Hvordan sikrede I sporbarhed gennem artefakter?
?
Sporbarhed blev sikret ved brug af modeller såsom BPMN, domænemodeller og DCD.
    - Fx blev en use case som _Organiser medarbejderdata_ først repræsenteret i objekt-og domænemodeller, derefter i SSD og til sidst reflekteret i DCD og implementeringen.
    - På denne måde kan vi se en rød tråd fra krav til implementering.

Hvordan har I kommunikeret jeres løsning?
?
Vi har dokumenteret systemet med modeller og rapporter og brugt domænespecifikke termer for klarhed.

Hvordan har I arbejdet med kvalitetssikring?
?
Vi arbejdede med kvalitetssikring gennem løbende reviews i GitHub, hvor hver pull request blev evalueret. 
Derudover brugte vi domænemodeller og design-class diagrammer for at undgå designfejl.

Hvordan blev modeller brugt til at forstå problemdomænet?
?
BPMN-modellen hjalp os med at forstå den eksisterende ferieplanlægningsproces og identificere forbedringsområder, såsom reducering af manuelt arbejde og risiko for fejl.

Hvordan har I brugt modeller til analyse og design?
?
- Analyse: BPMN blev brugt til at kortlægge ferieplanlægningsprocessen, som gav os et klart billede af krav og interessenter.
- Design: Domænemodellen blev skabt for at identificere vigtige objekter som `Employee` og `VacationRequest`, som blev implementeret i både databasen og koden.

Hvordan sikrer jeres løsning værdi for virksomheden?
?
Systemet reducerer manuel planlægning fra uger til sekunder, hvilket frigiver ressourcer og skaber en mere retfærdig fordeling. 
Dette blev illustreret i BPMN-modellen, som sammenlignede den nuværende og foreslåede proces.

Hvordan har I arbejdet med interessenter?
?
  Vi samarbejdede med flere aktører fra Alfa Laval (warehouse manager, projektleder og team manager), hvilket hjalp os med at forstå deres forskellige krav.
     - Warehouse manager ønskede simpelt UI.
    - Projektleder fokuserede på tekniske detaljer.
    - Team manager ønskede effektivitet og retfærdighed.

Overvejelser om GDPR?
?
- GDPR ikke håndteret pga. klare instrukser fra Alfa Laval.
- Foreslåede GDPR-tiltag:
    1. Kryptering af data.
    2. Sletning/anonymisering ved brugerens anmodning.
    3. Indhentning af samtykke.

Hvordan har I vurderet virksomhedens forretningsprocesser?
?
Ved at analysere virksomhedens workflow gennem BPMN-modellen og fokusere på automatisering af ferieplanlægning.

Hvorfor kun BPMN og ikke BMC/business case?
?
- Fokus på procesoptimering, ikke salg af idé.
- BPMN gav overblik over eksisterende og fremtidige processer.

Hvordan har I designet brugergrænsefladen, og hvad er vigtigt her?
?
Vi designede UI’et med fokus på enkelhed og funktionalitet, med FURBS+ i baghovedet.
    - Eksempel: Lederens dashboard giver overblik over ferieønsker og muligheden for at generere ferieplaner intuitivt.


Hvordan argumenterer I for projektets værdi?
?
- **Tidsbesparelse:** Fra uger til sekunder.
- **Retfærdighed:** Automatisk fordeling mindsker fejl.
- **Brugervenlighed:** Let at anvende for ledere.



Hvordan valgte I softwarearkitekturen, og hvorfor MVVM?
?
Vi valgte MVVM, fordi det er velegnet til WPF-applikationer, giver adskillelse mellem UI og forretningslogik, og gør test og vedligeholdelse lettere.


Hvordan designede I brugergrænsefladen?
?
Vi brugte wireframes, som blev itereret i tæt samarbejde med Alfa Laval. Fokus var på simpelt design og få klik for brugerne.


**Hvordan har I evalueret kvaliteten af jeres løsning?**
?
Kvaliteten blev evalueret gennem test af algoritmen, brugervenligheden af UI’et, og gennem feedback fra Alfa Laval.


**Hvordan adresserer systemet menneskelig interaktion i virksomheden?**
?
Systemet automatiserer ferieplanlægning, hvilket reducerer stress og frustration for ledelsen og medarbejderne.


**Hvordan vil I anbefale Alfa Laval at implementere løsningen?**
?
Start med pilotprojekter for at tilpasse systemet og træne brugerne. Overvej fremtidige behov som integration med eksisterende HR-systemer.


**Hvordan sikrede I, at IT og forretningsprocesser er sammenhængende?**
?
BPMN-modellen hjalp med at binde IT-løsningen til de faktiske forretningsprocesser, så systemet understøtter virksomhedens daglige drift.

Hvordan har I arbejdet med systemudviklingsmetoder?
?
Vi brugte Scrum-inspirerede metoder med iterationer og stand-ups for at sikre løbende fremdrift.
    - GitHub Projects hjalp med opgavestyring og sporbarhed.

Hvordan har eksperimenter hjulpet i jeres systemudvikling?
?
- **Svar:** Vi eksperimenterede med forskellige algoritmer til ferieallokering for at finde den mest retfærdige løsning.
    - Fx testede vi, hvordan randomisering af medarbejdere med samme prioritet forbedrede fairness.

 Hvorfor var Use-Case 2 særligt problematisk?
?
- **Kompleksitet:** Use-Case 2 dækker tre konceptuelle klasser:
    - `Lagermedarbejder`
    - `Kompetence`
    - `Ferieønske`  
    Disse klasser udgør størstedelen af modellaget i vores program og krævede hver især betydeligt arbejde.
- **Scope:** Use-casen var for bred til at passe ind i ét sprint og burde være opdelt i tre separate use-cases eller sprints.
- **Læring:** Vi indså undervejs, at opdeling ville have gjort arbejdsprocessen mere overskuelig og mindsket overlap mellem klasserne.

Hvordan kunne Use-Case 2 have været opdelt for at mindske problemerne?
?
- Opdelingen kunne have været baseret på de tre konceptuelle klasser:
    1. **Lagermedarbejdere:** Fokus på at oprette og vedligeholde medarbejderdata.
    2. **Kompetencer:** Sikre, at hver medarbejder har korrekt tilknyttede kompetencer.
    3. **Ferieønsker:** Håndtering af medarbejdernes ønsker og validering af input.
- **Fordel ved opdeling:**
    - Mindre afhængighed mellem klasserne i udviklingsprocessen.
    - Mulighed for hurtigere levering af delmål, hvilket kunne give hurtig feedback fra interessenter.

Hvordan påvirkede ændringer i kravene fra interessenter Use-Case 2?
?
- **Sen ændring:** Alfa Laval ønskede en funktion, hvor lagermedarbejdere selv kunne indtaste ferieønsker, frem for at dette blev håndteret af lederen.
- **Effekt:**
    - Ændringen blev tilføjet i systemet, men ikke repræsenteret i use-casen eller modellerne pga. tidsmangel.
    - Vi vurderede, at det ikke påvirkede de centrale stamdata eller systemets kernefunktioner, hvorfor vi ikke opdaterede dokumentationen.

Hvordan kan erfaringerne fra Use-Case 2 bruges fremadrettet?
?
- **Bedre opdeling:**
    - Fremover ville vi sikre, at komplekse use-cases opdeles i mindre, selvstændige use-cases, hver med et klart scope og mål.
- **Iterativ dokumentation:**
    - Ændringer i kravene ville blive reflekteret i modeller og use-cases, så dokumentationen altid er opdateret.
- **Tættere samarbejde:**
    - Tættere dialog med interessenter kunne have hjulpet med at forudse ændringer og planlægge for dem tidligere i processen.

Hvilken værdi havde modellerne ud over dokumentation?
?
- Modellerne fungerede som et kommunikationsværktøj:
    - De hjalp med at sikre, at alle i gruppen havde samme forståelse af, hvordan systemet skulle designes.
    - De gav overblik over relationer mellem klasser, som hjalp os med at undgå designfejl.


#flashcards/Eksamensprojekt/Tværfagligt
Hvad ville I ændre med mere tid?
?
- **Algoritmeoptimering:** Bedre allokering og håndtering af flere parametre.
- **Flere funktioner:**
    - Sletning af kompetencer og ferietyper, selv hvis de er i brug.
    - Fejlmeddelelser og bedre UI.
- **Mobilvenlighed:** Tilgængelighed på flere platforme.

Hvordan har I samarbejdet som et  team?
?
- Roller blev fordelt baseret på vores styrker (fx algoritmer, UI-design, og database).
- Samarbejde blev understøttet af GitHub til versionsstyring og løbende kodeintegration.

#flashcards/Eksamensprojekt/Algoritmen
Hvordan sikrer algoritmen fairness i allokeringen?
?
- Medarbejdere grupperes efter sidste års prioritet, og rækkefølgen inden for grupper randomiseres.
- Ferieønsker prioriteres i stigende rækkefølge, så medarbejdere med højere prioritet får førsteret.

Hvordan håndterer algoritmen bemandings- og kompetencekrav?
?
- Før hver ferieallokering tjekkes, om bemandingskravet og kompetencekrav kan opfyldes, hvis ønsket tildeles.
- Hvis nogen krav brydes, afvises ønsket.

Hvorfor er bemandingskravet transformeret fra procent til en absolut værdi?
?
- Transformationen gør det muligt at arbejde med faktiske tal (antal medarbejdere) fremfor procent, hvilket forenkler beregningerne.

Hvordan kunne algoritmen forbedres?
?
- **Performance**: Optimer kørslen ved at reducere gentagne opslag i lister.
- **UI-forbedringer**: Gør det nemmere for brugere at justere input (f.eks. dynamisk valg af kompetencekrav).

Hvordan hænger flowchartet sammen med algoritmen?
?
- Flowchartet repræsenterer hovedtrinene i algoritmen:
    - Sortering af medarbejdere.
    - Validering og allokering af ferie.
    - Opdatering af lister for bemanding/kompetence og generering af output.

Hvilke input har algoritmen?
?
- Liste over arbejdsdage og minimumsbemanding pr. dag.
- Medarbejderliste med kompetencer og ferieønsker.
- Specifik ferietype.

Hvilke output har algoritmen?
?
- CSV-fil, der viser ferieplanen for hver medarbejder.
- Status på opfyldelse af bemandings- og kompetencekrav.

Forklar flowet i algoritmen
?
- Validering → Transformation → Sortering → Allokering → Generering af output.