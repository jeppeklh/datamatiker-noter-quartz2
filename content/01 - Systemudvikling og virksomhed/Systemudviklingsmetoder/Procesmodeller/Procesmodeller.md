

>[!tldr] Definition  
En procesmodel er en skabelon, der hjælper med at planlægge og styre, hvornår og hvordan aktiviteter i et softwareudviklingsprojekt udføres. Den angiver rækkefølgen af faser (såsom kravspecifikation, design, implementering, test og vedligeholdelse) og fungerer som en vejledning til at strukturere processen.

## Lineære Procesmodeller
---
[[00 - Lineære Modeller|Lineære Modeller]] følger en fast, sekventiel rækkefølge, hvor hver fase afsluttes fuldstændigt, før den næste påbegyndes. Der er ingen mulighed for at gå tilbage til en tidligere fase.

> [!example] Eksempler
>
>- **Vandfaldsmodellen:** Hver fase (krav, design, implementering, test, vedligeholdelse) udføres trin for trin uden overlap.
>- **Vandfald med Overlap / Sashimi-modellen:** Tillader et vist overlap mellem faser, så nogle aktiviteter kan starte, før den foregående fase er helt afsluttet.
>- **Vandfald med Feedback:** Integrerer feedbacksløjfer, så man kan vende tilbage til tidligere faser for at rette fejl eller tilpasse krav, selvom den overordnede struktur forbliver sekventiel.

**Fordele ved lineære modeller:**
- Enkel og letforståelig struktur.
- Klare milepæle og kontrolpunkter, der sikrer forudsigelig planlægning.
- Velegnet til projekter med stabile og klart definerede krav.

**Ulemper ved lineære modeller:**
- Manglende fleksibilitet – ændringer eller fejl, der opdages sent, kan være dyre at rette.
- Risiko for, at fejl og misforståelser først identificeres i de senere faser, hvilket kan påvirke hele projektet.

## Cykliske Procesmodeller
---
[[00 - Cykliske Modeller|Cykliske Modeller]] (ofte kaldet iterative eller inkrementelle modeller) bygger på gentagne cyklusser, hvor man udvikler, evaluerer og forbedrer systemet løbende. Denne tilgang understøtter kontinuerlig feedback og tilpasning, så systemet kan justeres i takt med ændringer i krav og forretningsmiljø.
> [!example] Eksempel
>
>- **Agile:** Starter med et Minimal Viable Product (MVP) – den mindste version af systemet, som stadig giver værdi – hvorefter systemet udvikles organisk. Her øges fidelity (nøjagtigheden i forhold til design) på eksisterende dele, mens nye features tilføjes med lav fidelity og derefter forfines.
>- **Iterativ:** Systemet udvikles i gentagne cyklusser, hvor hver cyklus bygger videre på den forrige. Væksten i systemet drives af den værdi, som den enkelte cyklus leverer, og prioriteres ofte af repræsentanter for brugerorganisationen.
>- **Inkrementel:** Udviklingen foregår i separate, sammenhængende inkrementer. Hvert inkrement udarbejdes med høj fidelity og fuld funktionalitet, hvorefter det integreres med de andre dele. Denne model gør det muligt at refaktorere og forbedre systemet løbende, samtidig med at man leverer fuldt fungerende dele.

**Fordele ved cykliske modeller:**
- Høj fleksibilitet og evne til at tilpasse sig ændringer og nye krav.
- Tidlig og løbende feedback, som gør det muligt at identificere og rette fejl tidligt.
- Mulighed for gradvis udvikling, hvor hver iteration bidrager til systemets samlede værdi.

**Ulemper ved cykliske modeller:**
- Mere kompleks planlægning og styring, da kontinuerlig kommunikation og feedback er nødvendigt.
- Risiko for "scope creep", hvis ændringer ikke håndteres ordentligt.
- Det kan være vanskeligt at forudsige den endelige tidslinje og omkostninger.

## Systemets Vækst – Features og Fidelity
---
Når du vælger en cyklisk procesmodel, skal du også tage stilling til, hvordan systemet vokser over tid. Væksten måles typisk ud fra to parametre:

### Fidelity (Troskab)
- **Definition:** Fidelity refererer til, hvor nøjagtigt det udviklede system stemmer overens med det oprindelige design og de specificerede krav.
- **Anvendelse:** Høj fidelity betyder, at systemet er tro mod designkoncepterne, mens lav fidelity indikerer afvigelser eller mangler.
- **Eksempel:** Hvis brugergrænsefladens visuelle design præcist matcher de specificerede skitser, har systemet høj fidelity.

### Features (Funktioner)
- **Definition:** Features er de konkrete funktioner eller egenskaber, som brugerne kan interagere med.
- **Anvendelse:** Features dækker over de forskellige dele af systemet, såsom brugergrænseflader, databaser, integrationsmuligheder osv.
- **Eksempel:** Et e-handelswebsted kan have features som produktvisning, indkøbskurv, betalingsmuligheder og brugerprofiler.

### Vækstmodeller i cykliske processer
- **Agil:** Starter med et MVP og udvikler systemet organisk. Væksten sker både ved at forbedre eksisterende funktionalitet (øge fidelity) og ved at tilføje nye features, ofte i en organisk, “naturlig” vækstproces.
- **Iterativ:** Gentagne cyklusser, hvor hver iteration bygger videre på den forrige. Væksten kan foregå spredt på både features og fidelity, med prioritering baseret på den værdi, det giver for brugeren.
- **Inkrementel:** Udviklingen foregår i adskilte, fuldt færdige inkrementer. Hvert inkrement leveres med høj fidelity og integreres løbende med de øvrige dele af systemet, hvilket muliggør refaktorering og optimering undervejs.

## Sammenfatning
---
Valget af procesmodel – lineær eller cyklisk – afhænger af projektets krav, kompleksitet og behov for fleksibilitet. Lineære modeller tilbyder en struktureret og forudsigelig tilgang, mens cykliske modeller understøtter løbende tilpasning og systemudvikling gennem iterationer, hvor systemets vækst vurderes i forhold til både funktioner og fidelity.


> [!example] Eksempel
>
**Forestil dig, at du er ejendomsudvikler, der bygger et nabolag med 100 huse. Hvordan vil hver af de lineær, cyklisk, incremental og agile approaches svare til boligsalg?**
>
>- **Lineær**: Byg alle huse, før du begynder at sælge nogen.
>- **Cyklisk**: Byg et lille antal huse, forfin baseret på feedback, og udvid derefter.
>- **Incremental**: Sælg og færdiggør én sektion af huse ad gangen.
>- **Agile**: Juster løbende husfunktioner og layout baseret på køberfeedback.
>
>Ejendomsudviklere bruger typisk den incrementelle approach.

> [!example] Eksempel 2
>
**Forestil dig, at du er en anden ejendomsudvikler, der specialiserer sig i mere interessante projekter. Denne gang bygger du en forlystelsespark. Hvordan vil hver af de lineære, cykliske, incrementelle og agile approaches svare til åbningen af parken?**
>
>- **Lineær**: Byg hele parken, før den åbnes for besøgende.
>- **Cyklisk**: Åbn en sektion af parken, forfin attraktionerne, og udvid derefter.
>- **Incremental**: Åbn én forlystelse ad gangen for offentligheden.
>- **Agile**: Forbedr løbende attraktionerne baseret på besøgsfeedback.
>
>Typisk følger forlystelsesparker den incrementelle approach, hvor nye attraktioner tilføjes over tid.

## Procesmodel vs. Systemudviklingsmetode
---
En procesmodel er en abstrakt beskrivelse af, hvordan de forskellige faser i udviklingsarbejdet hænger sammen – for eksempel om du følger en sekventiel (predictive) eller en iterativ tilgang. Den fokuserer på rækkefølgen af aktiviteter som kravindsamling, design, implementering, test og vedligeholdelse.

En systemudviklingsmetode dækker derimod hele tilgangen til at udvikle et system. Det inkluderer ikke blot procesmodellen, men også de konkrete teknikker, værktøjer, roller og arbejdsmetoder, der anvendes for at opnå et færdigt produkt. Med andre ord er procesmodellen en delmængde af den samlede systemudviklingsmetode, som også indeholder de praktiske redskaber og retningslinjer, der hjælper med at styre og gennemføre projektet.

## Resourser
---
- [Procesmodeller Læringsobjekt](https://rise.articulate.com/share/-uAiD1CvlEXdENbkMn17_PJLTwFakBcP#/)


