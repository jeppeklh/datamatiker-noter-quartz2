### Workflow Overblik
1. **PR Pipeline:**
    - **Trigger:** En pull request (PR) i Azure Repos Git.
    - **Checks:**  
        - Bygning af koden (inklusive afhængigheder).  
        - Statisk kodeanalyse, linting, sikkerhedsscanning og unit tests.
    - **Flow:**  
        - Hvis en check fejler, stoppes PR’en, og udvikleren skal rette fejlene før merge.
    - **Review:**  
        - Efter at alle checks er godkendt, kræves en PR-gennemgang inden merge.

2. **CI Pipeline:**    
    - **Trigger:** Når koden merges til hovedbranch (trunk/main).
    - **Checks:**  
        - Udfører de samme kontroller som PR-pipelinen, med tilføjelsen af integrationstests.  
        - Integrationstestsne kører post-merge for at fange eventuelle nye problemer.
    - **Resultat:**  
        - Ved succes publiceres buildartefakter, som videre benyttes i CD.

3. **CD Pipeline:**    
    - **Trigger:** Udgivelse af artefakter fra CI-pipelinen.
    - **Deployment til Staging:** – Artefakter downloades og deployeres til et stagingmiljø.  
        - Acceptance tests køres for at validere deploymentet. – Valgfri manuel validering kan tilføjes før den næste fase.
    - **Deployment til Produktion:** – Efter manuel intervention (eller automatisk hvis ikke implementeret) deployeres løsningen til produktion.  
        - Smoke tests køres for at sikre, at produktionen fungerer som forventet.
    - **Rollback:**  
        - Hvis tests fejler, udløses en rollback, og udvikleren underrettes for at foretage rettelser.
        
---

### Overvågning og Sikkerhed
- **Monitoring:**  
    - Azure Monitor, Application Insights og Log Analytics anvendes til at indsamle data om systemets sundhed, performance og anvendelse.
    
- **Sikkerhed:**  
    - Azure Key Vault integreres for at hente og håndtere følsomme data, så hemmeligheder ikke eksponeres i pipelines.
    
- **Agentvalg:**  
    - Overvej om du vil bruge Microsoft-hosted eller self-hosted agents afhængigt af sikkerheds- og performancekrav.

---

## Resourcer
- [Azure Pipeline Microsoft Documentation](https://learn.microsoft.com/en-us/azure/devops/pipelines/architectures/devops-pipelines-baseline-architecture?view=azure-devops)