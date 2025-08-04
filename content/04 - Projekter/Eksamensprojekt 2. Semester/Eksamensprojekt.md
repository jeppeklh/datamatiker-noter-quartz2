



ALLE artefakter og kode skal være i rapporten. 

Vi bliver bedømt på alt i rapporten. 
Ikke nødvendigvis det der står i produktet-

Udvælg 1 use case of følg den til dørs. også relevante stored procedures osv.

Vise produkt og reflektion i repæsentationer. 
Snak om en uscase fra start til slut



Reflektioner
Stored procedure failsafes (Startdate skal være mindre en Enddate).

Kig på VacationTypeVVM. Noget af logikken er flyttet udi VacationTypeVVM. SRP i form af at VacationTypeVVM manipulerer dataen. CreateOrUpdate- og DeleteVVMs står for at håndtere input. Logikken sker så i VacationTypeVVM.



Giver ikke rigtig mening at lave med BMC - alfa laval er en kæmpe virksomhed. og vi ved alleredee hvordan vi skaber værdi for virksomheden.

Vi skal ikke sælge os selv til virksomheden så mange af de andre virksomheds modeller passer ikke rigtig på dette projekt.

BPMN - det kunne være den kunne hjælpe. Skal formuleres sådan og ikke: Vi ved at det ikke virker men vi gør det for en sikkerheds skyld.

Test i læringsmål er Pending Review. 

Kort præsentatiopn af projeket (case og hvad projektet går ud på).
Live demonstrattion af SCRUM (github projects, med tasks, issues og feature branching).
Læg fokus p de ting vi er stolte af. 


### **1. Modeller at inkludere**

#### **BPMN (Business Process Model and Notation):**

- **Relevans:**
    - Giver en detaljeret forståelse af arbejdsgange, som er centrale for et ferieplanlægningsprogram.
    - Kan hjælpe med at identificere flaskehalse i processen, fx hvis godkendelsesprocedurer tager for lang tid.
- **Hvorfor:** Da jeres projekt handler om procesoptimering (fx ansøgning og godkendelse af ferier), er BPMN uundværlig for at kortlægge og optimere disse arbejdsgange.

#### **Interessentanalyse:**

- **Relevans:**
    - Sikrer, at I tager højde for forskellige interessenters behov og krav, fx HR-afdelingen, medarbejdere og ledelse.
- **Hvorfor:** Interessentanalyse er nødvendig for at sikre, at løsningen bliver brugervenlig og opfylder alle målgruppers forventninger.

#### **Business Case:**

- **Relevans:**
    - Viser projektets økonomiske og strategiske værdi, som kan overbevise ledelsen om at investere i løsningen.
- **Hvorfor:** En business case giver mulighed for at beregne ROI og tidsbesparelser, hvilket er vigtigt for at vise projektets relevans.

---

### **2. Modeller der kan udelades**

#### **BMC (Business Model Canvas):**

- **Argument for udeladelse:**
    - BMC er primært designet til at analysere og udvikle forretningsmodeller – fx hvordan en virksomhed skaber, leverer og fanger værdi.
    - Jeres projekt er mere teknisk orienteret og handler om at udvikle et værktøj, der understøtter eksisterende forretningsprocesser (ferieplanlægning), ikke om at ændre virksomhedens forretningsmodel.
    - Mange af de indsigter, BMC kunne bidrage med, kan opnås gennem interessentanalyse og en business case. For eksempel:
        - **Kundesegmenter:** Interessentanalyse afdækker allerede målgrupper som HR og medarbejdere.
        - **Værdiforslag:** Dette kunne være analyseret gennem interviews eller kravspecifikationer uden at bruge BMC.
    - Derfor kan BMC anses som overflødig, da dens funktioner overlapper med andre værktøjer.

---

### **Hvordan opnår vi BMC's formål uden at bruge BMC?**

BMC bruges til at kortlægge:

1. **Kundesegmenter:** Hvem skaber vi værdi for? (Kan afdækkes i interessentanalyse.)
2. **Værdiforslag:** Hvilket problem løser vi? (Kan afdækkes i kravspecifikationer og business case.)
3. **Kanaler:** Hvordan når vi kunderne? (Ikke direkte relevant for et internt værktøj.)
4. **Indtægts- og omkostningsstruktur:** Hvordan skaber og fanger vi værdi? (Dækkes af business case.)

Ved at kombinere interessentanalyse og business case har I allerede dækket de relevante aspekter af BMC, uden at I behøver selve modellen.

---

### **Anbefaling**

Tag **BPMN**, **interessentanalyse**, og **business case** med i jeres projekt, da de er direkte anvendelige. Udelad BMC, da dens funktioner overlapper med de andre værktøjer, og dens primære fokus på forretningsmodeludvikling ikke er kernerelevant for jeres projekt.

### **Business Case: Ferieplanlægningsprogram**

#### **Baggrund og formål:**

Virksomheden oplever ineffektivitet og frustration med den nuværende proces for ferieplanlægning. Ferieansøgninger bliver ofte forsinket, og HR bruger unødigt meget tid på at administrere ferier manuelt. Et nyt digitalt system til ferieplanlægning kan løse disse udfordringer ved at automatisere og optimere processen.

#### **Mål:**

- Reducere tidsforbruget på ferieadministration med 50%.
- Forbedre medarbejdertilfredsheden ved at gøre ansøgnings- og godkendelsesprocessen mere brugervenlig.
- Integrere løsningen med eksisterende HR-systemer.

#### **Fordele:**

- **Øget effektivitet:** Automatisering sparer tid for HR og ledere.
- **Fejlreduktion:** Mindre risiko for dobbeltbookinger og manuelle fejl.
- **Skalerbarhed:** Kan tilpasses virksomheder med varierende antal medarbejdere.
- **Dataintegration:** Automatisk synkronisering med løn- og arbejdstidssystemer.

#### **Udgifter:**

- **Udviklingsomkostninger:** 250.000 kr.
- **Implementering og træning:** 50.000 kr.
- **Vedligeholdelse:** 30.000 kr. årligt.

#### **Forventet ROI:**

- Tidsbesparelse: HR og ledere sparer samlet 1.000 timer årligt (værdi: 300.000 kr.).
- Forbedret medarbejderproduktivitet og tilfredshed.

#### **Risici:**

- Teknologisk risiko: Integration med eksisterende systemer kan tage længere tid end forventet.
- Brugeraccept: Medarbejdere og ledere skal vænne sig til det nye system.

#### **Konklusion:**

Investeringen på 300.000 kr. forventes at være tilbagebetalt inden for ét år på grund af tidsbesparelser og øget effektivitet. Implementeringen vil skabe en mere brugervenlig og pålidelig proces for ferieplanlægning.

---

### **Interessentanalyse: Ferieplanlægningsprogram**

|**Interessentgruppe**|**Interesser**|**Indflydelse**|**Hvordan imødekommes deres behov?**|
|---|---|---|---|
|**HR-afdelingen**|Effektivitet, mindre administrativ byrde|Høj|Automatisering af ferieansøgninger og rapportering.|
|**Medarbejdere**|Brugervenlighed, gennemsigtighed i ferieplanlægning|Høj|Intuitivt design, mulighed for at se ferieoversigt.|
|**Ledelsen**|Økonomiske besparelser, overblik over fravær|Høj|Rapporter om ferieforbrug og fremtidige behov.|
|**IT-afdelingen**|Systemintegration, sikkerhed|Middel|API'er og sikkerhedsfunktioner, fx kryptering af data.|
|**Ledere/teamchefer**|Enkel godkendelsesproces, minimal tidsspild|Høj|Hurtig godkendelse via notifikationer og workflows.|

---

### **Eksempler på anvendelse i praksis:**

1. **HR-afdelingen:**
    - Med det nye program kan HR hurtigt trække rapporter over ferieforbrug, uden at skulle søge manuelt i regneark.
2. **Medarbejdere:**
    - De kan ansøge om ferie via en brugervenlig app og få status på deres ansøgninger i realtid.
3. **Ledelsen:**
    - Økonomiske rapporter fra business casen vil vise dem, hvor meget virksomheden sparer, og hvordan ressourcer udnyttes bedre.





## Reflektioner
---
Vi har fået fortalt at gøre det på den her måde, men vi har gjort det på denne måde fordi...