
## SSD
Dette SSD repræsenterer detaljer fra Use Case 2, som specificerer ledernes handlinger.

Diagrammet fokuserer på interaktionen mellem lederen og systemet for håndtering af ferieønsker. Systemets funktionalitet bliver skitseret, uden at gå i detaljer om, hvordan data internt behandles.
Leder repræsenterer den eksterne aktør, der opretter, redigerer og viser ferieønsker.
Systemet behandler ferieønsker og returnerer information til lederen.
Diagrammet viser tre forskellige scenarier:

Oprettelse af ferieønske
Leder starter oprettelsen af et ferieønske ved at sende en forespørgsel til systemet. Systemet bekræfter oprettelsen og returnerer det indtastede ferieønske til lederen.

Visning af ferieønsker
Leder anmoder om visning af eksisterende ferieønsker. Systmet hener og returnerer de oprettede ferieønsker til lederen.

Redigering af ferieønsker
Lederen vælger et ferieønske at redigere og ændrer de relevante data. Systemet registerer ændringerne, opdaterer og viser ferieønskerne.

SSD'en viser tydeligt sammenhængen mellem lederen og systems handlinger, uden at gå i detaljer. Dette gør diagrammet nyttigt, til at visualisere de vigtigste hændelser, og flowet mellem brugeren og systemet. 

Diagrammet fungerer desuden som grundlag for at udarbejde operationskontrakter, som er nødvendige for specificere systemets funktionalitet.

Skal usecasen også beskrive indhentning af data??

---

## SD
Sekvensdiagrammet giver en visuel repærsentationaf, hvordan data relateret til feireønsker håndteres i systemet. SD'er beskriver hvordan brugeren interagerer med applikation, fra åbning af systemet til indhentning og visning af ferieønsker. 

Diagrammet viser en linær sekvens af handlinger, hvor systemet håndterer forskillige trin i forbindelse med indhentning af ferieønsker. Brugeren åbner først applikationen, hvilket aktiverer systemets forskellige lag, der initierer og henter data fra systemets database. 
Der fremhæves hvordan forskellige komponenter som MainWindow, MainVV og VacationRequestVM arbejder sammen for at levere data til brugeren. 

SD'et bruges til at dynamisk visualisere nogle af de komplekse processer involveret i håndtering af ferieønsker. Diagrammet viser tydeligt rækkefølgen af operationer, og hvordan data bevæger sig mellem de forskellige lag i systemet i realtid. 
Dette hjælper os som udviklere med at forstå systemets arbejdsproces og de forskillige trin, der udføres for at sikre korrekt behandling af data.

Har brugt brugeren her i stedet for leder (Aktør hedder også User i SD her men Leder i andre artefakter)

---

## Databasemodel
Databasemodellen hjælper os med struktureret at organisere data og har dannet grundlaget for implementeringen af vores RDBMS - vores SQL database. 
Den er desuden blevet normaliseret efter de 3 første normalformer, for at sikre dataintegriget og nøjagtighed. 

Databasemodellen illustrer strukturen af de data, der skal persisteres i systemets database.
Hver tabel i modellen repræsenterer en entitet, der indeholder attributter, som oversættes til SQL-kolonner med tilhørende datatyper. 

Eksempelvis indeholder EMPLOYEE-entiteten kolonner som employee_id (primærnægle), employee_name, employee_number, is_day_shift og student.
Relationerne og kardinalitet mellem tabellerne vises gennem associationer i modellen. 

I modellen er tabellen SKILL_SET designet til at understøtte dynamisk opdatering af kolonner. Dette er vigtigt, fordi kravene til medarbejderenes kompetencer kan ændre sig over tid, og systemet skal derfor kunne tilpasse sig. Eksempelvis, hvis der kommer et behov for en ny kompetence som "Førstehjælp", kan kolonnen oprettes via. programmet.
Dynamikken i SKILL_SET er illusretet ved hjælp af tre prikker (...) under attributlisten. 
Når systemt oprettes, starter tabellen med en enkelt kolonne, employee_id, som er den sammensatte primærnøgle, med en fremmednøgle-relation. Yderligere kolionner kan derefter tildøjes dynamisk under kørsel eller ved hjælp af scripts, der kører efter deployment.

Vi har brugt Databasemodellen som et vigtigt værktøj i kommunikationen med Alfa Laval. Modellen gjorde det muligt for os at præsentere, hvordan vi håndterer og strukturerer dataene, og det har hjulpet os med at afstemme forventninger og krav. Det gav en visuel forståelse af systemets dataopbygning og en mulighed for feedback, inden fuld implementation af databasen.

Skal vi nævne, at beskeden om, at Alfa Laval ønskede muligheden for at tilføje kompetencer, først blev givet senere i udviklingsprocessen, og skal det står her?

Undervejs i udviklingsprocessen blev det klart, at Alfa Laval ønskede muligheden for dynamisk at kunne tilføje kompetencer i SKILL_SET-tabellen. Denne besked kom sent i processen, hvilket førte til en nødvendig omlægning af den oprindelige databasearkitektur. 
I stedet for at designe en statisk model med foruddefinerede kolonner til kompetencer, valgte vi en løsning, der tillader dynamiske opdateringer af kolonner. 
Hvis dette krav var blevet kommunikeret tildligere i processen, kunne vi have overvejet alternative løsninger, såsom at modellere kompetencer i en separat tabel. Dette ville have reduceret afhængigheden af dynamiske kolonneændringer.

TAL OM VIGTIGHEDEN AF TIDLIG KRAVSPECIFICERING.


Hvorfor har vi den og hvad bruger vi den til?
vi har delt den med alfalaval og brugt den til kommunikation




FURBS+ og SMART har være centrale principper i udviklingen af vores løsning. Vi har gennem hele projektet brugt FURBS+ til at sikre, at vores software er funktionel, brugervenlighed og pålidelig. Brugervenlighed har særligt været et fokusområde, hvor vi med ugangpunkt i wireframes designede en grænseflade, der undgår for meget information på skærmen. Erfaringer fra tidligere projekter hjalp os med at holde vinduer overskuelige og intuitive. 
SMART-principperne hjalp os med at styre projektet ved at opstille måbare og klare mål, eksempelvis ved implementeringen af Repositories, som blev færdiggjort indenfor en fastlagt tidsramme. Gennem denne tilgang har vi fra start til slut hold fokus på både kundes krav og en brugervenlig og holdbar løsning.
