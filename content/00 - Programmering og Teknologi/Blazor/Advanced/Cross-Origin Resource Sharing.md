---
aliases:
  - CORS
---
# CORS (Cross-Origin Resource Sharing)

> [!tldr] Definition
En mekanisme, der giver webservere mulighed for at specificere, hvilke eksterne domæner der må tilgå deres ressourcer. 
Det er en vigtig sikkerhedsfunktion, der hjælper med at forhindre uautoriserede eller ondsindede anmodninger fra andre domæner, samtidig med at den tillader kontrolleret adgang til API'er og andre ressourcer.


## Hvad er CORS?
---
Browsere håndhæver en politik kaldet **Same-Origin Policy**, som begrænser, hvordan dokumenter eller scripts fra et domæne kan interagere med ressourcer fra et andet. CORS løser denne begrænsning ved at lade serveren angive specifikke regler for, hvilke domæner der må foretage anmodninger.

### Centrale HTTP-headere:
---
- **Access-Control-Allow-Origin:** Angiver, hvilke domæner der har adgang til ressourcen. Eksempel: `"https://example.com"` eller `"*"` for at tillade alle.
- **Access-Control-Allow-Methods:** Specificerer, hvilke HTTP-metoder (GET, POST, PUT, DELETE osv.) der er tilladt.
- **Access-Control-Allow-Headers:** Angiver, hvilke HTTP-headere klienten må sende.
- **Access-Control-Allow-Credentials:** Tillader, at cookies og andre legitimationsoplysninger sendes med anmodninger.
- **Access-Control-Max-Age:** Bestemmer, hvor længe resultaterne af en preflight-anmodning kan caches.


### Relevans for Blazor
---
- **Blazor WebAssembly**: Kører i browseren og sender HTTP-anmodninger til en back-end API (ofte på et andet domæne). Uden korrekt CORS-konfiguration på serveren blokerer browseren disse anmodninger.

> [!example] Eksempel
Hvis din Blazor-app på [https://blazor-app.com](https://blazor-app.com/) skal kalde en API på [https://api.example.com](https://api.example.com/), skal API'en tillade anmodninger fra [https://blazor-app.com](https://blazor-app.com/) via CORS-headers.

## Hvorfor er CORS vigtigt?
---
- **Sikkerhed:** Ved at begrænse, hvilke domæner der kan få adgang til dine ressourcer, reducerer CORS risikoen for uautoriserede anmodninger og potentielle sikkerhedstrusler som f.eks. CSRF (Cross-Site Request Forgery).
- **Kontrolleret Deling:** Du kan præcist definere, hvem der må tilgå din API eller dine ressourcer, og under hvilke betingelser.
- **Udviklingsfleksibilitet:** Det bliver muligt at udvikle applikationer, der kommunikerer med API'er på tværs af domæner, når reglerne er korrekt konfigureret.


## Konfiguration af CORS i ASP.NET Core
---
I ASP.NET Core kan du konfigurere CORS via `Startup.cs` (eller `Program.cs` i nyere versioner). Herunder er et par eksempler:

### Eksempel 1: Tillad et specifikt domæne
---
**Program.cs:**
```csharp
var builder = WebApplication.CreateBuilder(args);

// Tilføj CORS-tjenester og konfigurer en politik
builder.Services.AddCors(options =>
{
    options.AddPolicy("AllowSpecificOrigin", policy =>
    {
        policy.WithOrigins("https://example.com")
              .AllowAnyHeader()
              .AllowAnyMethod();
    });
});

builder.Services.AddControllers();

var app = builder.Build();

app.UseRouting();

// Anvend CORS-politikken
app.UseCors("AllowSpecificOrigin");

app.UseEndpoints(endpoints =>
{
    endpoints.MapControllers();
});

app.Run();

```
I dette eksempel tillader vi udelukkende anmodninger fra `https://example.com` og giver adgang til alle metoder og headere.

Metoder er her alle actionmethods , altså HTTP-protokoller som GET POST osv.
Headers

**Headers** er metadata, der sendes med en HTTP-anmodning (request) eller et svar (response). De indeholder ekstra information, som hjælper serveren og klienten med at kommunikere korrekt.
- **Hvem der sender anmodningen** (User-Agent, Origin)
- **Hvilket format anmodningen har** (Content-Type)
### Eksempel 2: Tillad flere domæner og credentials
---
Hvis du skal tillade flere domæner og have mulighed for at sende cookies eller andre credentials, kan du konfigurere CORS som følger:
```csharp
var builder = WebApplication.CreateBuilder(args);

// Tilføj CORS-tjenester og konfigurer en politik, der tillader flere domæner og credentials
builder.Services.AddCors(options =>
{
    options.AddPolicy("AllowMultipleOrigins", policy =>
    {
        policy.WithOrigins("https://example.com", "https://anotherdomain.com")
              .AllowAnyHeader()
              .AllowAnyMethod()
              .AllowCredentials(); // Gør det muligt at sende cookies
    });
});

builder.Services.AddControllers();

var app = builder.Build();

app.UseRouting();

app.UseCors("AllowMultipleOrigins");

app.UseEndpoints(endpoints =>
{
    endpoints.MapControllers();
});

app.Run();

```
Her specificeres to tilladte domæner, og vi tillader, at credentials sendes med anmodningerne.

## Preflight Requests
---
For komplekse anmodninger (såsom dem med metoder som PUT, DELETE eller anmodninger med brugerdefinerede headere) sender browseren først en **preflight**-anmodning med HTTP-metoden OPTIONS. Denne anmodning kontrollerer, om serveren accepterer den egentlige anmodning ved at se på de angivne CORS-headere. Serveren skal svare med de korrekte tilladelser, før browseren fortsætter med den egentlige anmodning.



## Opsummering
---
- **CORS** er en central mekanisme, der definerer, hvordan ressourcer kan deles mellem forskellige domæner.
- **Same-Origin Policy** beskytter mod uautoriserede anmodninger, mens CORS giver kontrolleret adgang ved at definere specifikke regler.
- I **ASP.NET Core** kan du nemt konfigurere CORS via `services.AddCors()` og `app.UseCors()`.
- Preflight-anmodninger sikrer, at komplekse anmodninger kun sendes, når de overholder de definerede sikkerhedsregler.

## Resourcer
---
- [Blazor WebAssembly Læringsobjekt (CORS)](https://scorm.itslearning.com/data/3289/C20150/ims_import_38/scormcontent/index.html#/lessons/BteImlY66O1cDAtgfjL-ZesFTMHQvpiu)
- [Blazor WebAssembly LinkedIn Kursus (CORS)](https://www.linkedin.com/learning/blazor-webassembly-foundational-skills/cross-origin-resource-sharing-cors?resume=false&u=57075649)
- [Blazor Sikkerhed Læringsobjekt (CORS)](https://scorm.itslearning.com/data/3289/C20150/ims_import_41/scormcontent/index.html#/lessons/vHoDf8CJz0qFMikvmpJ1PGHbMoLjbnWM)
- [CORS Youtube video](https://www.youtube.com/watch?v=4KHiSt0oLJ0&t=136s&ab_channel=Fireship)