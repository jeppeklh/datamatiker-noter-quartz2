###  Direkte API-kald vs. API-gateway
---
##### Hvilke sikkerhedsrisici ser du ved ikke at have en intern gateway?
Uden en gateway er applikationen direkte afhængig af, at de eksterne API'er er stabile og sikre. Det betyder:

- Ingen rate limiting eller request validering centralt.
- Hver komponent skal selv håndtere fejl og autorisation.
- Et DDoS-angreb på et enkelt eksternt API kan nedlægge hele løsningen.

##### Hvordan ville en API-gateway konkret kunne beskytte jer mod DDoS-angreb?
Gatewayen fungerer som et centraliseret filter, der:

- Begrænser antallet af kald per klient (rate limiting).
- Kan køre bag en reverse proxy med cache og WAF (Web Application Firewall).
- Afkobler frontenden fra backenden, så angreb ikke rammer direkte.


##### Hvad gjorde JWT-komplekst i jeres løsning?
Vi brugte ASP.NET Identity, som er tæt bundet til cookie-baseret login. JWT kræver manuel håndtering af:

- Token generation og validering.
- Fornyelse af tokens (refresh tokens).
- Opbevaring på klienten (localStorage/cookies med ekstra sikkerhed).


### Cookie-baseret login og ASP.NET Identity
---
##### Hvordan beskytter cookies mod session hijacking?
Cookies kan beskyttes med:

- `HttpOnly`: gør det umuligt for JavaScript at læse dem.
    
- `Secure`: sikrer at de kun sendes over HTTPS.
    
- `SameSite`: reducerer risiko for CSRF.
    

##### Hvordan håndterer I session timeout og token fornyelse?
ASP.NET Identity styrer dette automatisk. Sessionen udløber efter en periode (fx 20 minutter), og brugeren bliver bedt om at logge ind igen. Der bruges sliding expiration.

##### Har I overvejet CSRF – og hvordan håndterer I det?
Ja. ASP.NET Identity har indbygget AntiForgeryToken til formularer, og `SameSite` cookies hjælper også. Vi sikrer, at alle POST-requests validerer tokens.


### Adgangskontrol og rolleopdeling
---
##### Hvordan sikrer du, at roller ikke kan eskaleres af en angriber?
Kun admins har adgang til UI og controller-metoder der tildeler roller. Vi bruger `[Authorize(Roles = "Admin")]` på disse endpoints.

 ##### Hvordan valideres rollerne server-side? 
Roller valideres i ASP.NET Identity via Claims i cookie’en, som kontrolleres i controlleren ved hjælp af `[Authorize]` attributten.


### EF Core og SQL Injection
---
##### Hvordan kan man omgå EF Core og skrive farlig SQL?
Hvis man bruger `context.Database.ExecuteSqlRaw()` uden parameterisering, kan man få SQL injection. Derfor undgår vi raw SQL og bruger LINQ.

##### Er der tilfælde, hvor parameterisering ikke er nok?  
Hvis man dynamisk sammensætter hele SQL-sætninger med brugerinput, kan det stadig være risikabelt, især hvis man overskriver EF's sikkerhedsmodeller.

---

### Audit-log og brute-force detection
---
##### Hvordan gemmes logdata?  
Planen er at logge til en database eller fil via fx Serilog. Logs kan analyseres manuelt eller integreres med et overvågningsværktøj som ELK stack.

##### Hvordan opdager I brute-force?
Ved at analysere mange mislykkede loginforsøg fra samme IP eller konto i kort tid. Det kunne fx føre til midlertidig IP-blokering.


### Backup og recovery
---
##### Hvor ofte tager I backup – og af hvad?
Vi tager backup af databasen og brugerkonto-data med faste intervaller (fx dagligt). Kildekoden er versionsstyret i Git.

##### Hvordan tester I, at backup virker? 
Vi gendanner backup i et testmiljø og verificerer, at data og brugerkonti kan tilgås og fungerer korrekt.


### MFA og fremtidig udvidelse
---
##### Hvordan vil MFA implementeres i praksis?  
Via ASP.NET Identity + f.eks. SMS-kode eller app-baseret (Microsoft Authenticator). Brugeren tilføjer en 2. faktor i deres profil.

##### I hvilke situationer bliver MFA nødvendigt?
Når platformen udvides til håndtering af følsomme data, eller hvis virksomheden får krav via GDPR, NIS2 eller opererer i sektorer med høj compliance (f.eks. finans, sundhed).


## Mere om API
---
### **Fordele og ulemper ved direkte API-kald fra Blazor Server**

**Fordele:**

- **Simpel arkitektur**: Mindre kompleksitet og hurtigere udvikling.
    
- **Ingen behov for CORS-konfiguration** (når alt kører på samme domæne/server).
    
- **Mindre latency**: Ét hop frem for to (gateway → service).
    

**Ulemper:**

- **Sikkerhedsrisiko**: Direkte kald betyder, at fejl i API-håndtering eller overbelastning kan forplante sig direkte til din app.
    
- **Tæt kobling**: Appen bliver afhængig af API’ernes tilgængelighed og kontrakter.
    
- **Manglende skalerbarhed/genbrug**: Du kan ikke nemt tilføje flere klienter, som også skal bruge samme data.
    
- **Sværere at centralisere logging, rate limiting, og validering.**
    

---

### **Mulige risici ved direkte API-kald uden mellemlag**

1. **Ondsindet JSON (f.eks. med script-injektion)**
    
    - Hvis din applikation parser JSON direkte og f.eks. viser noget i UI’et uden sanitering, kan der opstå XSS (cross-site scripting).
        
    - Eksempel: Et API returnerer `"name": "<script>alert('hack')</script>"`, og du viser det i en Blazor-komponent uden `@sanitize`.
        
2. **Deserialization angreb**
    
    - Hvis du deserialiserer JSON til objekter (med `System.Text.Json` eller `Newtonsoft.Json`) uden at validere input, kan det føre til _injection-angreb_, specielt hvis du tillader polymorfi eller bruger `TypeNameHandling`.
        
3. **Overbelastning via store payloads**
    
    - En angriber kan sende meget store JSON-payloads og få serveren til at bruge meget CPU/memory.
        
4. **API trust-problemer**
    
    - Hvis det eksterne API returnerer data, du stoler på (uden kontrol), kan det manipulere din app. F.eks. returnere uventede felter eller manglende felter – som din app ikke er robust overfor.
        

#### Hvordan en API-gateway (eller intern service) hjælper

- **Validering af payloads** (model validation, schema-checks)
    
- **Central sanitering af output**, så al HTML/tekst renses før det sendes videre til UI
    
- **Rate-limiting og size-throttling**, som beskytter mod store JSON payloads
    
- **Logging og afvisning af “farlige” mønstre**, som script-tags, lange inputs, null bytes osv


---
### **Hvornår bør man bruge en intern API-gateway/producer-consumer arkitektur?**

**Anvendelsesområder:**

- Når **flere klienter** (f.eks. mobile apps, web apps, admin dashboards) skal tilgå samme data.
    
- Når du har behov for **central validering, logging og sikkerhedspolitikker**.
    
- Ved **microservice-arkitektur**, hvor forskellige services skal interagere med hinanden.
    
- Når du vil **beskytte bagvedliggende services** mod direkte adgang, f.eks. ved rate-limiting og caching.
    
- Når du arbejder med **service mesh, distribueret tracing** eller skalerbare API-strukturer.
    

**Eksempler på setup:**

- Frontend → API Gateway (Producer) → Interne services (Consumers)
    
- Gateway’en har controllers, autentificering, logging og videresender kald til “consumers”
    
- Consumer services har ikke UI, men kun logik og adgang til data (typisk REST eller gRPC)
    

---

### **Typisk setup i .NET (Producer-Consumer/Backend-For-Frontend)**

1. **Frontend (Blazor WebAssembly/Server)**: UI-komponent, sender kald til `ApiController`.
    
2. **API Gateway (Producer)**: .NET Web API-projekt med controllers, sikkerhed og middleware.
    
3. **Services (Consumer)**: Interne services med domænelogik og datalagring – typisk injected via DI.
    
4. **Data layer**: EF Core eller anden ORM.
   
   
### **Begreberne "producer" og "consumer"**
   
I API-arkitektur bruges _producer_ ofte om den service, der “udstiller” en API, og _consumer_ om dem, der bruger den (fx din frontend eller en anden microservice).