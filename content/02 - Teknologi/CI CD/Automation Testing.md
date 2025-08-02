---
aliases:
  - Automation Tests
  - Automation Test
---
> [!tldr] Definition
> Automation testing er brugen af specialiserede værktøjer eller scripts til automatisk at køre prædefinerede tests på en softwareapplikation.   

- **Formål:**  
    - Eliminere manuel indgriben ved gentagende testopgaver (fx regressionstests)  
    - Forbedre testeffektivitet og dække et bredere testområde
        
- **Resultat:**  
    - Hurtigere testudførelse  
    - Forøget nøjagtighed og konsistens i testresultaterne  
	 - Frigørelse af ressourcer til mere komplekse testaktiviteter
        
---

## Fordele ved Automation Testing
- **Omkostningsbesparelser:**  
    Reducerer langsigtede omkostninger ved at minimere manuel indsats og forkorte udviklingscyklusser.
    
- **Tidlig Fejlfinding:**  
    Identificerer fejl på et tidligt stadium, hvilket reducerer omkostninger og indsats til at rette problemer senere i udviklingsprocessen.
    
- **Hurtigere Feedback:**  
    Automatiserede tests giver øjeblikkelig feedback, hvilket muliggør hurtigere beslutningstagning og kortere udviklingstider.
    
- **Bedre Ressourceudnyttelse:**  
    Frigør teams fra monotone, gentagende opgaver, så de kan fokusere på komplekse og kreative testopgaver.
    
- **Forbedret Nøjagtighed:**  
    Maskinbaserede tests eliminerer menneskelige fejl, hvilket sikrer pålidelige og reproducerbare testresultater.
    
- **Øget Testdækning:**  
    Automatiserede tests kan dække flere scenarier og data-sæt, hvilket fører til en grundigere validering af systemet.
    
- **Øget Testhastighed:**  
    Automatiserede tests kører betydeligt hurtigere end manuelle tests – særligt vigtige ved regression og belastningstest.
    
- **Højere ROI:**  
    Hurtigere releases og bedre kvalitet, med færre manuelle testomkostninger, medfører en højere samlet investeringsafkast.
    
---

## Automation Testing vs. Manuel Test

|**Aspekt**|**Manuel Test**|**Automation Testing**|
|---|---|---|
|**Nøjagtighed**|Høj risiko for menneskelige fejl|Høj nøjagtighed – fejlfri maskinbaseret testning|
|**Skalerbarhed**|Kan tage lang tid ved stor skala|Udfører tests i stor skala med høj effektivitet|
|**Turnaroundtid**|Længere cyklusser|Hurtigere cyklusser – ideelt for tidkrævende regressionstests|
|**Omkostningseffektivitet**|Dyrere i forhold til ekspertiseomkostninger|Besparelser over tid, når infrastrukturen er oppe at køre|
|**Brugeroplevelse**|Afhænger af menneskelig observation og vurdering|Mangler menneskelig intuition, men garanterer konsistens|
|**Område for specialisering**|Udføres typisk for eksplorativ, ad-hoc og usability tests|Ideel til regression, performance og gentagne testkørsler|
|**Færdigheder**|Kræver evnen til at imitere brugeradfærd|Kræver programmering og scripting-evner for testcase-automatisering|

---

## Hvilke Tests Skal Automatiseres?
Følgende tests egner sig særligt godt til automatisering:

- **Repetitive og Monotone Tests:**  
    Fx regression og smoke tests, som køres gentagne gange med samme testflow.
    
- **Data-drevne Tests:**  
    Testscenarier, der kræver mange datasæt – fx formularvalidering og database tests.
    
- **Forretningskritiske Tests:**  
    Tests der validerer kernefunktionaliteter, som har stor indflydelse på forretningsdriften.
    
- **Deterministiske Tests:**  
    Testcases med klare pass/fail-kriterier, fx UI-valideringer og API-respons-check.
    
- **Cross-platform og Miljø Tests:**  
    Tests, der skal eksekveres på flere operativsystemer, browsere eller enheder for at sikre kompatibilitet.
    
- **Tidskrævende og Kedelige Tests:**  
    Fx performance- og belastningstests, som ved manuel udførelse kan være ekstremt arbejdskrævende.
    
---

## Typer af Automation Testing
Her er en oversigt over de mest almindelige testtyper, der kan automatiseres:

- **Regression Testing:**  
    Kontinuerlig kørsel af tests, som sikrer, at nye funktioner ikke forstyrrer eksisterende funktionalitet.
    
- **Smoke Testing:**  
    Hurtig validering af de vigtigste systemfunktioner for at afgøre, om en build er værd at teste nærmere.
    
- **Data-drevet Testing:**  
    Automatiserede tests, der validerer funktionaliteter med varierende datasæt for konsistens.
    
- **Performance Testing:**  
    Test af applikationens ydeevne under forskellige belastninger og forhold.
    
- **Functional Testing:**  
    Test af systemets funktionalitet ved hver PR (pull request) for at give hurtig feedback på kodeændringer.
    
- **Security Testing:**  
    Automatiseret scanning for sårbarheder og sikkerhedshuller i applikationen.
    
- **Acceptance Testing:**  
    Sikrer, at softwaren lever op til forretningsmæssige krav og kravene fra slutbrugerne.
    
- **API Testing:**  
    Validering af funktionalitet, sikkerhed og pålidelighed af applikationens API'er.
    
- **UI Testing:**  
    Sikrer, at brugergrænsefladens elementer (knapper, felter og layouts) fungerer korrekt og giver en glidende brugeroplevelse.
    
---

## Opsummering
Automation testing er en hjørnesten i moderne softwareudvikling, der:

- **Reducerer omkostninger og testtid** ved at automatisere gentagne og tidskrævende testopgaver.
    
- **Forbedrer kvaliteten og dækningen** af tests ved at køre et bredt spektrum af scenarier uden menneskelige fejl.
    
- **Giver hurtigere feedback** til udviklere og QA-teams, hvilket muliggør hurtigere iterationer og beslutninger.
    
- **Udvider testskalaen** og sikrer kompatibilitet på tværs af platforme og enheder.
    

Noterne giver et overblik over, hvad automation testing indebærer, de konkrete fordele sammenlignet med manuel test, og hvilke testtyper samt testscenarier der bør prioriteres for at opnå optimal testeffektivitet.

---

## Resourcer
- [Automation Testing Aritcle](https://www.browserstack.com/guide/automation-testing-tutorial)