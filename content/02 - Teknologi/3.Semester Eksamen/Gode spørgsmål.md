###  Sikkerhed
---
**Hvordan håndterer I autentifikation og autorisation?**  
Vi bruger **Blazor Identity** til at håndtere autentifikation. Der er tre roller i systemet: _Customer_, _Employee_ og _Admin_.  
Vi bruger **policy-baseret autorisation**, så kun brugere med bestemte roller kan tilgå visse sider og funktioner. F.eks. er admin-sider kun tilgængelige for brugere med rollen "Admin".

**Hvordan har I beskyttet systemet mod kendte trusler (f.eks. SQL injection, XSS)?**  
Vi bruger **Entity Framework**, som er et ORM (Object-Relational Mapper). Det sikrer, at alle SQL-forespørgsler bliver parameteriseret, hvilket beskytter mod SQL Injection.  
Mod XSS har vi bl.a. undgået direkte HTML-rendering af brugerinput og stoler generelt ikke på data fra brugeren.

**Hvordan logger og overvåger I jeres system?**  
Vi har ikke implementeret central logning fra databasen, men vi har bygget en simpel **logningsløsning i C#**, som registrerer mislykkede loginforsøg.  
Dataen gemmes i databasen og vises på et **admin-dashboard**. Hvis en bruger har mere end 10 mislykkede loginforsøg på en time, bliver det markeret med en rød indikator – som en form for **simpel DDoS/dictionary attack-beskyttelse**.

**Hvad ville I gøre, hvis vi opdagede et sikkerhedsbrud i vores løsning?**  
Først ville vi **identificere og isolere problemet**, f.eks. ved at deaktivere en API eller brugerkonto.  
Derefter ville vi:

1. **Gennemgå logs** for at forstå omfanget.
2. **Blokere mistænkelig IP-trafik** (f.eks. via firewall).
3. **Informere relevante personer** – både internt og evt. brugere.
4. Tage en backup og **genskabe systemet** fra før bruddet, hvis nødvendigt.
5. Implementere **forbedringer** – f.eks. rate limiting, stærkere autentifikation, bedre logning.

Vi kunne følge en struktur som i en rigtig **incident response-plan**: identifikation → afhjælpning → kommunikation → forebyggelse.


### Docker
---
**Hvad er Docker, og hvorfor valgte I det?**  
Docker er en platform til at køre applikationer i isolerede containere. Det gør det nemt at sikre, at applikationen kører ens på alle maskiner – både lokalt og i produktion.  
Vi brugte Docker til at køre en **SQL Server-container** i udviklingen, fordi det var hurtigere og nemmere end at installere SQL Server manuelt.

**Hvordan er jeres applikation containeriseret?**  
Applikationen er ikke fuldt containeriseret, men vi har brugt en **SQL Server-container**, som blev kørt via **Docker Compose** i udviklingsfasen.  
Senere er både app og database blevet **hostet i skyen på Azure**, og Docker blev ikke nødvendigt i den endelige deployment.

**Hvordan håndterer I netværk og kommunikation mellem containere?**  
Vi brugte **Docker Compose**, som automatisk sætter containere i samme netværk, så de kan kommunikere via container-navne.  
I vores tilfælde kunne applikationen f.eks. tilgå databasen på `sqlserver:1433`.

**Hvilke fordele og ulemper oplevede I ved at bruge Docker?**  

**Fordele:**
- Hurtig opsætning af udviklingsmiljø.
- Ingen behov for lokal SQL Server-installation.
- Let at "nulstille" miljøet.  

**Ulemper:**
- Ekstra kompleksitet, især for nybegyndere.
- Ved flere containere kan det kræve mere konfiguration (volumes, netværk osv.).
  
**Hvorfor har vi kun containeriseret SQL Server og ikke vores app?**  
Det var en **prioritering**. SQL Server var tung at installere lokalt, så det gav mening at containerisere den. Vores app blev i stedet deployet direkte til Azure.  
**Fordele ved kun at containerisere databasen:** Simpelt, hurtigt og dækker det vigtigste behov.  
**Ulemper:** App og database er ikke fuldt isoleret sammen – det kan give problemer, hvis man vil køre hele stacken lokalt eller i staging.  
**Der er en grund til at containerisere begge dele**: Det giver konsistens og gør det nemmere at automatisere alt i CI/CD – f.eks. spin-up af testmiljøer.

###  CI/CD
---
**Hvordan har I implementeret CI/CD i jeres projekt?**  
Vi har sat en **CI/CD-pipeline** op, som bygger og tester projektet automatisk ved **push eller merge til main**. Derefter bliver der **automatisk deployet til Azure**.

**Hvilke trin består jeres pipeline af?**  
Vores pipeline består af tre trin:

- **Build:** Projektet bliver bygget for at sikre, at det kompilerer.
    
- **Test:** Unit og integrationstests bliver kørt.
    
- **Deploy:** Applikationen bliver automatisk rullet ud til Azure.
    

**Hvordan tester I jeres kode automatisk?**  
Vores **unit- og integrationstests** bliver automatisk kørt i pipelinen ved merge/push til `main`-branchen.

**Hvordan håndterer I deployment (eks. staging vs. production)?**  
Vi har ikke opdelt i staging og production. Der bliver **deployet direkte til Azure**, når noget kommer på `main`. I et større projekt kunne det være en fordel at have staging-miljø til test og godkendelse, inden produktion.

CI/CD automatiserer både test og deployment. Det betyder, at:
- Fejl fanges **tidligt**, når tests fejler.
- Deployment er **ensartet og pålidelig**, da det sker automatisk.
- Vi undgår "it works on my machine"-problemer.  
    Det gør hele udviklingsforløbet mere stabilt og giver hurtigere feedback.
    
**Hvordan har I tænkt sikkerhed ind i CI/CD-processen (DevSecOps)?**  
Vi har ikke integreret automatiske sikkerhedsscanninger, men vi har tænkt sikkerhed ind i koden:

- Vi bruger Identity og policies.
- Vi logger loginforsøg.  

I fremtiden kunne vi tilføje **dependency scanning** og **secret scanning** (f.eks. med GitHub Actions eller SonarCloud), så vi fanger sårbarheder automatisk i CI-processen.

### Generelle spørgsmål med refleksion
---
**Hvis I skulle gøre det igen – hvad ville I gøre anderledes?**  
Vi ville nok sørge for at containerisere hele applikationen fra starten – f.eks. med Docker Compose til både frontend, backend og database.  
Vi ville også gerne have implementeret mere central logning og bedre overvågning – f.eks. med et tool som **Serilog**, **Grafana** eller **Application Insights** i Azure.

**Hvad har I lært om samarbejde, automatisering eller sikkerhed under projektet?**  
Vi har lært, hvor vigtigt det er at tænke **sikkerhed og automatisering ind tidligt** i udviklingen. CI/CD og logging gjorde vores projekt mere robust og gav en følelse af kontrol.  
Desuden har vi lært værdien af **roller og adgangsstyring**, så kun de rigtige personer har adgang til de rigtige dele af systemet.

**Hvilken del af teknologistakken havde størst indflydelse på jeres projekt?**  
CI/CD og autorisation var centrale. CI/CD sikrede hurtig og stabil deployment, mens Identity og autorisation gjorde det muligt at beskytte systemets funktioner på en fleksibel måde.