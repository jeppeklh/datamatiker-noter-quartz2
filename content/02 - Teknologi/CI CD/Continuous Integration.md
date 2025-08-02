---
aliases:
  - CI
---

> [!tldr] Definition
> En udviklingspraksis, hvor udviklere regelmæssigt integrerer deres kode i en fælles codebase (ofte kaldet trunk, main eller mainline). > Hver integration udløser en build og automatiserede tests for at opdage fejl tidligt.

**Formål:**  
At sikre, at softwaren altid er i en fungerende tilstand og minimere risikoen for regressionsfejl ved at arbejde i små, hyppige trin.

---

### Vigtige Elementer i CI
- **Automatiseret Build Process:**  
    - Hvert commit udløser en build, som skal være nummereret, gentagelig og levere autoritative pakker.  
    - Eksempel: En build-script, der henter afhængigheder, kompilerer koden og genererer et deploybart artefakt.

- **[[Automatiserede Tests]]:**  
    - Unit tests og integrationstests, der køres automatisk for hver commit.  
    - Testene skal give feedback inden for få minutter for at holde iterationerne korte.  
    - Eksempel: Ved at bruge TDD (Test-Driven Development) sikrer man, at koden er modulær og nem at teste.

- **Feedback Mekanismer:**  
    - Synlige indikatorer (fx traTclights eller integration i et chat-system) informerer teamet om, hvorvidt en build er god eller brudt.  
    - Vigtigt at stoppe arbejdet og rette fejl med det samme, hvis en test fejler.

---

### Udfordringer og Faldgruber
- **Langvarige tests:**  
    - Tests, der tager for lang tid, kan forhindre hyppige integrationer.    
- **Manuel indgriben:**  
    - Manglende automatisering (fx i build-processer) øger risikoen for fejl.

- **Ikke daglig merge:**  
    - Hvis udviklere ikke merger deres arbejde til trunk dagligt, kan det føre til lange og komplekse integrationer.

---

## Resourcer
- [Continious Integration](https://dora.dev/capabilities/continuous-integration/)