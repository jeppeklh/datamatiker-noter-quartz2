---
aliases:
  - CD
---
> [!tldr] Definition
> Evnen til hurtigt og sikkert at frigive softwareændringer til produktion. Målet er, at systemet altid er deployable – både under normale forhold og under pres.

**Skelnen til Continuous Deployment:**  
Continuous Deployment er en videreudvikling, hvor hver kodeændring automatisk deployes til produktion, mens CD lægger vægt på at have en deploybar kodebase samt en kontrolleret frigivelse.
    
---

### Nøgleprincipper og Vigtige Elementer
- **Automatiseret Deployment:**  
    – Deployment-processen er fuldstændig automatiseret, så udrulning kan ske uden manuel indgriben.  
    – Eksempel: Et CD-pipeline, der downloader artefakter fra CI-pipelinen og deployer til staging og produktion.
    
- **Acceptance Tests og Smoke Tests:**  
    – Efter deployment køres tests i stagingmiljøet for at validere, at systemet fungerer korrekt.  
    – I produktion kan der køres smoke tests for at sikre, at udgivelsen er stabil.
    
- **Infrastruktur som Code (IaC):**  
    – Systemkonfigurationer og miljøopsætninger defineres og versionstyres som kode, hvilket sikrer konsistens og sporbarhed.
    
- **Tekniske Praksisser:**  
    – Inkluderer testautomatisering, version kontrol, og løbende overvågning, som samlet reducerer risikoen ved udrulninger.
    
---

### Fordele ved CD
- **Lavere Risici:**  
    – Softwaren er altid i en deploybar tilstand, og releases sker på en lav-risiko måde.
    
- **Hurtigere Feedback:**  
    – Hele systemets deployability valideres regelmæssigt, hvilket giver løbende feedback til teamet.
    
- **Forbedret Kvalitet og Produktivitet:**  
    – Med automatiserede tests, deployment og overvågning opnår man mere stabile systemer og reducerer behovet for rework.

---

## Resourcer
- [Continuous Delivery](https://dora.dev/capabilities/continuous-delivery/)