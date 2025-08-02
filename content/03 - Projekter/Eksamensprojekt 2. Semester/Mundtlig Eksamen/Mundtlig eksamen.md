## Svagheder og mangler ift. pensum i projektet
#### Ingen brug af nedarvning og abstraktion i koden
Vær klar til at forklare, hvordan arv kunne være implementeret i en fremtidig version. 
F.eks. ved at skabe en fælles klasse for alle typer anmodninger.


---

#### Ingen brug af threads/processer

Forklar, at algoritmens eksekveringstid er hurtig nok uden threads, men overvej hvordan det kunne implementeres for parallelle opgaver i fremtidige versioner.

---

#### Manglende TCL og triggers i SQL
Vi valgte transaktioner i applikationslaget frem for triggers for at bevare kontrol og undgå kompleks fejlfinding.

Vær klar til at forklare, hvorfor dette valg giver fleksibilitet, og hvordan triggers kunne skabe uforudsigelig adfærd.

---

#### Ingen kryptering eller sikkerhedsforanstaltninger
Der er ingen nævnt sikkerhed for følsomme medarbejderdata.
Overvej simple tilføjelser som hashing eller kryptering for passwords i fremtiden.

---

#### Ingen omfattende testning
Begrænset testdækning med kun få unit tests.
Forklar de udfordringer, vi mødte med databaseintegration, og overvej at nævne mock-databaser som en fremtidig løsning.

---

#### Kun én forretningsmodel
BPMN er brugt, men BMC, business case og interessentanalyse er udeladt.
Begrund fravalget med, at projektet ikke skulle sælges som en forretningsidé, og at vi arbejdede med klare krav fra starten.

---

## Mulige spørgsmål fra censor/vejleder
#### Om fravalgte teknologier og metoder
###### Hvorfor har I ikke brugt arv og polymorfi i koden?
Vi fokuserede på at bygge en løsning, der opfyldte Alfa Lavals krav, og i den nuværende implementering blev der ikke identificeret et akut behov for arv. Men i en fremtidig iteration ville det være oplagt at benytte arv i brugerhåndteringen, hvor vi kunne have en `Employee` som baseklasse og to nedarvede klasser: `RegularEmployee` og `Manager`.

- **`Employee`** ville indeholde fælles attributter som navn, ID og kompetencer.
- **`RegularEmployee`** kunne begrænses til at indsende ferieønsker og se sin egen ferieplan.
- **`Manager`** ville have ekstra rettigheder til at oprette og slette ferieønsker, tilføje eller fjerne medarbejdere og køre ferieplanlægningsalgoritmen.

Dette ville gøre systemet mere fleksibelt, hvis der senere skulle tilføjes flere brugerroller eller ændres i adgange.

###### Hvordan ville brugen af threads/processer forbedre systemet, hvis det blev skaleret op?
Vores nuværende løsning er designet til én bruger og en hurtig eksekveringstid på under et sekund. Dette gjorde det unødvendigt at implementere multithreading.  
Hvis systemet skulle håndtere mange samtidige brugere eller mere komplekse beregninger, kunne threads forbedre performance ved at udnytte flere CPU-kerner. Eksempelvis kunne ferieallokeringen køre som en baggrundsproces, så brugeren ikke skal vente på resultatet. Dette ville også gøre applikationen mere responsiv, da GUI’en kan forblive aktiv, mens beregningen kører i baggrunden.
###### Hvad ville fordelen være ved at bruge triggers frem for transaktioner i applikationen?
Triggers i SQL kan automatisk udføre logik, når bestemte hændelser opstår, som f.eks. ændringer i tabeller. Dette kan være nyttigt til at sikre datakonsistens.  
Vi valgte dog at implementere transaktionsstyring i applikationen, da det giver bedre kontrol over, hvordan og hvornår logik udføres. Transaktionerne kan debugges og justeres direkte i koden, hvilket gør det lettere at forstå og vedligeholde. Triggers kan til gengæld føre til uforudsigelige kædereaktioner, hvilket vi ønskede at undgå.

---

#### Om sikkerhed og datahåndtering
###### Hvordan sikrer I, at medarbejderdata behandles sikkert?
I projektet har vi ikke implementeret kryptering eller andre sikkerhedsforanstaltninger udover adgangskontrol, hvilket vi nævner som en begrænsning. 

**Adgangskontrol:** Rollebaseret adgang til applikationen, så kun autoriserede brugere kan se eller ændre data. Alm. medarbejdere kan kun se og ændre deres egne ferieønsker.

For at forbedre dette kunne vi anvende:
- **Kryptering:** Hashing af passwords og kryptering af følsomme data ved hjælp af AES eller lignende algoritmer.

###### Har I overvejet GDPR-implikationer?
Vi har ikke specificeret GDPR-tiltag, men vi er klar over, at medarbejderdata som ferieønsker og kompetencer kan være omfattet. Vi har fået fortalt af Alfa Laval at vi ikke skulle tage hensyn til GDPR-regler.

For at overholde GDPR skulle vi:

1. Sikre dataopbevaring med kryptering og begrænse adgang.
2. Implementere funktionalitet til at slette eller anonymisere data efter medarbejdernes ønske.
3. Sørge for samtykke til indsamling og brug af data.

---

#### Om forretningsmodeller
###### Hvorfor valgte I kun at inkludere BPMN og ikke en BMC eller business case?
Vi valgte BPMN, da det gav os et klart billede af de nuværende og foreslåede processer for ferieplanlægning. Vores fokus var at optimere en allerede eksisterende proces, frem for at sælge idéen eller udvikle en bredere forretningsstrategi.  
BMC og business case blev vurderet mindre relevante, da vi ikke skulle overbevise virksomheden om projektets værdi. Vi modtog i stedet en klar opgave fra virksomheden.
Fokus var på teknisk levering frem for strategisk udvikling, da løsningen var udformet til en eksisterende organisation og ikke en ny forretningsidé.
###### Hvordan ville I argumentere for projektets værdi overfor en leder eller investor?
Vores projekt reducerer ferieplanlægning fra flere ugers arbejde til et system, der kan generere en plan på få sekunder. Dette betyder:

- **Omkostningsbesparelser:** Mindre arbejdstid brugt på manuel planlægning.
- **Retfærdighed:** Automatisering eliminerer risiko for fejl og forskelsbehandling.
- **Brugervenlighed:** En intuitiv brugergrænseflade gør det nemt for ledelsen at anvende.

---

#### Om projektets begrænsninger og fremtidige udvikling
###### Hvad ville I ændre eller tilføje til systemet, hvis I havde mere tid?
- Implementere sikkerhedsmekanismer som kryptering og rollebaseret adgang.
- Udvikle funktioner til rapportering og statistikker, der kan hjælpe ledelsen med at evaluere ferieplanlægningen over tid.
- Tilføje en mobilvenlig version af applikationen for at gøre den mere tilgængelig.
###### Hvordan kunne I sikre skalerbarhed i jeres løsning, hvis det blev brugt i en større virksomhed?
For at sikre skalerbarhed kunne vi:
- **Brug af cloud-tjenester:** Flytte database og applikation til en cloud-løsning som Azure for at håndtere flere samtidige brugere.
- **Algoritmeoptimering:** Forbedre allokeringen, så den kan håndtere flere parametre eller reducere køretiden yderligere.
- **Funktionalitet:** 
    - Mulighed for at slette kompetencer og ferietyper, selv hvis de er i brug.
    - Bedre håndtering af fejl og brugervenlige fejlmeddelelser.
- **Brugeroplevelse:** Forbedre UI, så det bliver mere intuitivt for både medarbejdere og ledere. Dette kunne inkludere værktøjer til bedre visualisering af ferieplaner eller forenklet navigation.

---

#### Om testning og kvalitetssikring
###### Hvorfor var testdækningen begrænset?
I starten forsøgte vi at strukturere tests, der indsatte data i databasen, testede det, og derefter slettede det igen for at bevare databasens oprindelige tilstand. Disse tests blev dog fjernet, da vi var usikre på, om dette var best practice, og det viste sig at være komplekst og tidskrævende. Som resultat har vi ikke tests på databaseniveau, hvilket vi i bakspejlet burde have prioriteret for at sikre en højere kvalitet og stabilitet i vores løsning.

Fremadrettet kunne vi anvende mock-databaser, der simulerer en database, så tests kan udføres uden at påvirke produktionsdata.
###### Hvordan ville I strukturere tests anderledes i et fremtidigt projekt?
- **Test andre lag:** Vi kunne have implementeret unit tests til:
    - Algoritmen: Sikre korrekt allokering ved at teste edge cases og datainput.
    - UI-logik: Validere, at knapper og kommandoer udfører forventede handlinger.
- **Brug af integrationstests:** Teste hele forløb fra input til output for at sikre, at data flyder korrekt mellem lagene.
- **Automatiserede tests:** Bruge mocking-frameworks som Moq til at teste repository-metoder uafhængigt af databasen. (Udenfor pensum-scope?)
- **Integrationstests:** Sikre, at CRUD-operationer fungerer korrekt i databasen.
- **UI-tests:** Automatiserede tests af brugergrænsefladen for at fange fejl i interaktionen mellem frontend og backend.

