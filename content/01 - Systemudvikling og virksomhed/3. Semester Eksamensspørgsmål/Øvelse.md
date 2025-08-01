#flashcards/Gotorz

Hvordan sikrede I kvalitet?
?
Vi arbejdede med kvalitet på to fronter:
- **Verificering** gennem kodestandarder, PR-gennemgang og systematiske tjeklister – fx med fokus på SOLID og konsistens i modeller og kode.
- **Test** blev brugt både til at sikre funktionalitet og til performance/stress-test i slutningen.
- Vi brugte også **verificering af artefakter** – fx tjekkede vi om sekvensdiagrammer stemte overens med UC og DCD.
- **Validering** skete gennem scenariegennemgange, sporbarhed og intern kravmatch – det sikrede, at vi byggede det rigtige system trods manglende brugerfeedback.



Hvordan håndterede I usikkerhed?
?
Vi havde flere typer usikkerhed:
- **Kravusikkerhed**, fordi vi ikke havde adgang til PO efter opstart – det løste vi ved at bruge intern validering, sporbarhed og løbende kravgennemgang.
- **Metode- og teknologiusikkerhed**, fordi vi lærte mange ting undervejs – vi håndterede det ved at starte lineært og skifte til cyklisk model under implementering.
- **Domænekompleksitet**, især pga. roller og adgangskontrol – vi brugte arkitekturmodeller og tydelig begrebsafklaring i domænemodellen.

Hvordan håndterede I kompleksitet?
?
Vi havde især kompleksitet i systemets struktur og funktion:
- Der var **flere roller med adgangskontrol**, og systemet skulle integrere flere funktioner og flows, som fx billetudveksling, betaling og brugerstyring.
- For at håndtere det, lagde vi vægt på at **modellere tidligt og grundigt**: domænemodellen hjalp os med begrebsklarhed, og DCD/pakkediagram skabte overblik over arkitektur og ansvar.
- Vi brugte **layered architecture** og sikrede lav kobling mellem komponenter.
- Vi brugte også **4+1-modellen** som støtteværktøj til at kontrollere kompleksiteten i både struktur og funktion.
    

> Kompleksitet blev altså håndteret gennem overblik, adskillelse af ansvar og verificering på arkitekturniveau.

Hvordan valgte I jeres metode?
?
Vi valgte at starte med en **lineær analyse- og designfase**, fordi vi havde brug for at forstå krav og systemarkitektur først.  
Under implementeringen skiftede vi til en **cyklisk inkrementel model**, hvor vi arbejdede per feature – det gav os fleksibilitet og passede godt, fordi systemet først giver værdi, når det næsten er færdigt.  
Vi valgte **inkrementel frem for agil**, da MVP ikke gav mening, og fordi vi havde brug for teknisk overblik før vi kunne begynde.



Hvordan sikrede I sporbarhed?
?
Vi koblede hvert krav til relevante artefakter: UC, domænemodel, DCD, SD, implementering og test.  
Når vi lavede en ny feature, tjekkede vi altid, om alle modeller og tests understøttede det oprindelige krav.  (validering)
 Det fungerede som **validering**, fordi det sikrede, at vi byggede det rigtige system baseret på kravene.  
Hvis noget ikke hang sammen – fx ved billetudveksling – gik vi tilbage og reviderede kravet.  
Vi brugte også sporbarhed **mellem artefakter** til **verificering** – fx om DCD og SD stemte overens.   Det skabte en rød tråd og gav tryghed for, at intet krav blev glemt eller misforstået.

Hvordan brugte I 4+1-modellen?
?
Vi brugte 4+1-modellen **implicit som både validerings- og verificeringsværktøj internt**, da vi ikke havde adgang til PO eller reelle brugere efter opstart.
- **Scenarie-view:** Use cases og sekvensdiagrammer blev brugt til at validere brugerflows og sikre, at systemet matchede de forretningsmæssige behov vi kendte.
- **Logical view:** Domænemodel og DCD hjalp os med at forstå og strukturere de centrale begreber – og vi brugte dem til at tjekke konsistens og dækning af krav.
- **Development view:** Package-diagram og kodearkitektur gav os et internt verificeringsgrundlag for struktur og ansvar – fx undgik vi cirkulære afhængigheder.
- **Physical view:** Deploymentdiagrammet blev brugt til at vurdere, om løsningen kunne implementeres teknisk realistisk, og om afhængigheder og netværksforhold var overskuelige.
Vi brugte use cases som **scenariebinding mellem views**, og tjekkede løbende, at nye features blev understøttet af de relevante modeller.  
På den måde fungerede 4+1 som en intern metode til at **sikre både retning (validering) og teknisk korrekthed (verificering)** – selv uden ekstern feedback.



## Din 3-4 minutters procesforklaring
---
> _I vores projekt har vi arbejdet med en systemudviklingsproces, der starter lineært og skifter til cyklisk inkrementel under implementering._

**Først lavede vi analyse og design:**

- Vi brugte FURPS+ og BPMN til at afklare krav og forstå domænet.
    
- Vi lavede brugssituationer og use cases ud fra kravene – det blev vores scenarier.
    
- Vi tegnede domænemodel, lo-fi DCD og databasedesign for at få overblik over systemets struktur.
    
- Vi lavede også wireframes for at visualisere UI-flow og brugeroplevelse.
    

**Så planlagde vi arbejdet:**

- Vi lavede en featureliste ud fra kravene – det blev vores backlog.
    
- Vi brugte planning poker og gantt-chart til at estimere og planlægge features.
    

**Under implementering skiftede vi til cyklisk inkrementel model:**

- For hver feature videreudviklede vi modellerne og opdaterede DCD, databasemodel og sekvensdiagram.
    
- Vi skrev test og kode skiftevis – så vidt muligt TDD – og brugte PR-gennemgang for at sikre kvalitet.
    
- Vi arbejdede med daglige scrums og brugte Kanban til at styre opgaverne.
    

**Til sidst lavede vi kvalitetssikring og handover:**

- Vi stress- og performancetestede systemet, og lavede en plan for parallel udrulning.
    
- Feedback fra brugere vil danne grundlag for videreudvikling og vedligehold.
    

**Kvalitetssikring, validering og verificering har været en integreret del:**

- Vi brugte tests både til at tjekke funktionalitet og til at sikre kravforståelse.
    
- Vi validerede alle artefakter mod krav og brugte 4+1-modellen som intern tjekliste.
    
- Sporbarhed mellem krav og artefakter var central for at sikre, at vi byggede det rigtige – og gjorde det rigtigt.