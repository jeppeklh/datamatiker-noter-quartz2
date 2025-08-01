

### Hvordan integrerer man security – DevSecOps?
---
DevSecOps handler om at tænke sikkerhed **tidligt og automatisk** i hele udviklingsforløbet – også i jeres pipeline. Her er nogle måder, I kan forbedre sikkerheden i jeres CI/CD pipeline:

**Security Scanning**
Tilføj trin der scanner for:
- Sårbarheder i afhængigheder (`dotnet list package --vulnerable`)
- Kodefejl (statisk analyse med f.eks. [SonarCloud](https://sonarcloud.io/))
- Secrets i kode (f.eks. [GitHub Secret scanning](https://docs.github.com/en/code-security/secret-scanning))


**Sikker test og validering**
- Kør automatiserede tests med fokus på sikkerhed (f.eks. inputvalidering, authentication flows).
- Overvej at inkludere trusselsmodellering.


**Brug `least privilege` i secrets**
- Sørg for at de tokens og secrets, der bruges i deployment, **kun har adgang til det nødvendige**.


**Logning og sporbarhed**
- Sørg for at pipelinen logger nok information, så fejl og potentielle angreb kan spores.
- Brug GitHub's `audit log` og artefakt-logning.


**Automatisk rollback**
Implementér rollback-strategi ved fejl i deploy (kan være næste skridt for jer).
  
  
  
## CI/CD og testing – hvorfor hænger det sammen?
---

CI/CD (Continuous Integration / Continuous Deployment) handler om **automatisk at bygge, teste og levere kode**. 

Derfor passer det perfekt sammen med:

**TDD (Test-Driven Development):**  
Hvor man **skriver tests før koden**. Pipelinen sikrer, at de tests altid bliver kørt ved hver ændring.
    
**Unit tests:**  
Små tests, der tester enkeltdele af din kode (f.eks. én metode). I bruger `dotnet test` – godt eksempel på unit testing i jeres pipeline.
    
**Smoke tests:**  
Simpel "kan det køre?"-test efter deploy – fx tjek at API'et svarer. Kan udvides i jeres deploy-job.

**Regressionstest:**  
Tester om gamle features stadig virker efter ny kode – kan også automatiseres i pipeline.

**Code coverage:**  
Måler hvor meget af jeres kode, der bliver dækket af tests. Jo højere, jo bedre. Brug fx Coverlet i .NET.


### Trunk Based Development & Small Batches
---
Vi arbejder fra én **main branch** (trunk), og integrerer ofte = **færre konflikter og hurtigere feedback**.

“Small batch” betyder, at vi kun laver **små ændringer ad gangen**, som hurtigt testes og deployes – og det er netop det CI/CD understøtter.


### Feature Flags
---
Feature flags gør det muligt at **slå nye features til/fra uden at deploye ny kode**.

**Eksempel** 
En ny funktion er klar i koden, men kun aktiv, hvis `FEATURE_CHAT` = true i en config. 
Det er smart ved CI/CD, fordi du kan deploye koden, **uden at aktivere funktionen** med det samme.


### Linting
---
Linting er automatiske tjek for **kodekvalitet og stil** – f.eks. manglende semikolon eller dårlige navne. Det forbedrer **læselighed og ensartethed**. Kan tilføjes med GitHub Actions (fx `dotnet-format` for C#).



### Secrets
---
Vi bruger allerede **GitHub Secrets** til vores Azure login – det er god praksis.  
Secrets beskytter følsomme data (API-nøgler, tokens) og **skal aldrig ligge i koden**.



### Overlevering og miljøopsætning
---
Hvis man kender Gotorz’ setup og Azure-miljø, kunne man **genskabe det lokalt** eller på ny cloudkonto med `Infrastructure as Code` (IaC).  
Fx med ARM-templates, Bicep eller Terraform. 
Det gør projektoverlevering **hurtigere og mere pålidelig**.