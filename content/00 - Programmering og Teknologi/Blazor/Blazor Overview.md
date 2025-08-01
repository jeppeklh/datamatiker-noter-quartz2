---
aliases:
  - Blazor
---
> [!tldr] Definition
En webteknologi fra Microsoft til at bygge interaktive hjemmesider med **C# og .NET** i stedet for JavaScript.
>
Bruger en **[[Blazor-komponenter|komponent]]baseret arkitektur**, hvor hver komponent indeholder både design og funktionalitet, hvilket gør koden genanvendelig og let at vedligeholde.
>
Benytter [[Razor]]-syntaks til visninger.

- **WebAssembly** muliggør kørsel af .NET-kode direkte i browseren, hvilket giver høj ydeevne uden behov for plugins.
- Kan integreres med **JavaScript**, så eksisterende biblioteker som Bootstrap kan bruges sammen med C#.
- Har indbyggede **sikkerhedsfunktioner** til at kontrollere adgang og beskytte data.

## Typisk Blazor-projektstruktur 
---
Et typisk Microsoft Blazor-projekt består af flere [[Blazor-komponenter|komponenter]] og følger en bestemt struktur, der gør det nemt at organisere og vedligeholde koden. 
### Client-projekt 
- **Program.cs:** Indgangspunktet for applikationen. Her konfigureres tjenester og root-komponenter. 
- **wwwroot:** Indeholder statiske filer som CSS, JavaScript og billeder. 
- **Pages:** Indeholder .razor-filer, der repræsenterer forskellige sider i applikationen. 
- **Shared:** Indeholder komponenter, der bruges på tværs af flere sider, f.eks. layoutkomponenter og navigationsmenuer. 
### Server-projekt (for Blazor WebAssembly-hosted løsning) 
- **Controllers:** Indeholder API-kontrollere, der håndterer HTTP-anmodninger. 
- **Program.cs og Startup.cs:** Konfigurerer serveren og middleware. 
- **appsettings.json:** Indeholder konfigurationsindstillinger for applikationen. 
### Shared-projekt 
- Indeholder fælles klasser, metoder og ressourcer, der deles mellem Client- og Server-projekterne. 
### Typiske Filer og Mapper 
- **Imports.razor:** Indeholder globale using-direktiver for Razor-komponenter. 
- **MainLayout.razor:** Definerer hovedlayoutet for applikationen. 
- **App.razor:** Definerer rodruten og router-komponenten. 
- **Index.razor:** Standard startside for applikationen.


## Resourcer
---
- [Blazor Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_36/scormcontent/index.html#/lessons/HZvsvIqmIeSEJpeTrnlTERuelWDsYEYD)
- [Blazor LinkedIn Kursus](https://www.linkedin.com/learning/front-end-web-development-with-dot-net/build-and-run-your-first-blazor-web-app?resume=false&u=57075649)
- [Blazor WebAssembly Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_38/scormcontent/index.html#/lessons/q7hlBlKoOkVEzZD8sat5HfnC_1OlocZZ)
- [Blazor Projekttyper Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_39/scormcontent/index.html#/lessons/cvMTsNz1mzTPtnlUTGfD6ZiMjJfDDtlH)