# HTML / CSS

## Øvelse 1
>[!info] Del teamet op i to mindre grupper, og brug **Ordet rundt** til at reflektere over begreberne:
> 
> - Forklar ordene ”**client**” og ”**server**” for hinanden.
> - Hvordan kommunikerer client og server med hinanden? Vær så specifik som mulig.
> - Hvad er HTML, CSS og Bootstrap og hvad bruges de til?
> - Hvad er en webside, webapplikation og ”native apps”? Forklar forskellen mellem dem.

Sørg for, at alle får mulighed for at tale
> [!question] Client vs. Server

> [!note] Svar
>- En **client** er den enhed, der anmoder om information (f.eks. en browser, der besøger en hjemmeside).
>- En **server** er den enhed, der håndterer anmodningen og sender data tilbage (f.eks. en webserver, der leverer en [[HTML Overview|HTML]]-side).

> [!question] Hvordan kommunikerer de?

> [!note] Svar
>- Clienten sender en **HTTP-request** til serveren.
>- Serveren behandler anmodningen og sender en **HTTP-response** tilbage med data (HTML, JSON, billeder osv.).

> [!question] Hvad er HTML, CSS og Bootstrap?

> [!note] Svar
>- **HTML**: Strukturen af en webside (f.eks. tekst, billeder, links).
>- **CSS**: Styling af websiden (farver, skrifttyper, layout).
>- **Bootstrap**: Et framework, der gør det lettere at designe responsive og flotte sider.

> [!question] Webside vs. Webapplikation vs. Native app

> [!note] Svar
>- **Webside**: Simpel [[HTML Overview|HTML]]/[[CSS]]/JavaScript, ofte informativ.
>- **Webapplikation**: Interaktiv hjemmeside (fx Facebook, Gmail).
>- **Native App**: Installeret app på en enhed (iOS/Android), kører direkte på operativsystemet.

---

## Øvelse 2
**ca. 15 min**

>[!info]  Ud fra hvad du har lært i videoerne, burde du kunne løse disse opgaver, hvis ikke er det ganske tilladt at google noget hjælp:
> 
> [https://www.w3schools.com/html/exercise.asp?filename=exercise_html_attributes1](https://www.w3schools.com/html/exercise.asp?filename=exercise_html_attributes1) (løs alle opgaverne).

---

## Øvelse 3
**ca. 40 min**

>[!question]  Løs disse fire opgaver
> 
> [https://teaching.codenation.com](https://teaching.codenation.com/)

---

## Øvelse 4
**ca. 40 min**

>[!question]  Løs disse to opgaver
>
> [https://gocoding.org/html-practice-exercises/](https://gocoding.org/html-practice-exercises/)

---

# MVC
## Øvelse 5
**ca. 15 min**

>[!question]  Skriv tre ting ned fra forberedelsen, som I synes var svært.
> 
> Brug CL-strukturen: ”Team-ordspind” til at hjælpe hinanden til en bedre forståelse af stoffet ved at tage hvert af de svære emner frem og tilføje underbegreber, symboler, forbindelser o.s.v.
>
> Bagefter tager vi et par stykker op i plenum.  
 
---

## Øvelse 6
**ca. 20 min**

>[!info]  Brug Ordet rundt til at reflektere over begreberne:
> 
> MVC-arkitektur
>
> - Routing
> - Paging
> - Sortering
> - Entity Framework

> [!question] Hvad er MVC?

>[!note] Svar
>- **Model-View-Controller** (MVC) er en arkitektur til at organisere kode.
>- **Model**: Data og logik (f.eks. database).
>- **View**: Det brugeren ser (HTML/CSS).
>- **Controller**: Håndterer brugerens handlinger og sender data til viewet.
>
> Routing, Paging, Sortering og Entity Framework
>
>- **Routing**: Bestemmer, hvilken URL der kalder hvilken controller.
>- **Paging**: Opdeling af data i sider (f.eks. 10 elementer pr. side).
>- **Sortering**: Rækkefølge af data (f.eks. alfabetisk).
>- **Entity Framework**: ORM (Object-Relational Mapping), der gør det nemmere at arbejde med databaser i C#.

---

## Øvelse 7
**ca. 60 min**

> [!note] 
> Lav tutorialen [Get started with ASP.NET Core MVC](https://learn.microsoft.com/en-gb/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-9.0&tabs=visual-studio) som gruppe. > Ræk hånden op, når/hvis hele gruppen er gået i stå.
> 
> Trinene er:
>
> - Get started
> - Add a controller
> - Add a view
> - Add a model
> - Work with a database (se seedfil nederst)
> - Controller actions and views
> - Add search
> - Add a new field
> - Add validation
> - Examine Details and Delete

---

## Øvelse 8
**ca. 10 min**

>[!question]  Forklar følgende stump kode på skrift ord for ord:
> ```csharp
> public async Task<IActionResult> Indecx(string searchString) 
> { 
> 	var movies = from m in :_context.Movie select m; 
>	
>	if (!String.IsNullOrEmpty(searchString)) 
>	{ 
>		movies = movies.Where(s => s.Title!.Contains(searchString)); 
>	} 
>	
>	return View(await movies.ToListAsync()); 
> }
> ```

> [!note] Svar
> Koden er en **asynkron metode** i en **controller** i et ASP.NET Core [[MVC]]-projekt. Den håndterer søgning i en liste af film:
>- Der oprettes en forespørgsel, der henter alle film fra databasen.
>- Hvis brugeren har indtastet en søgetekst, filtreres listen, så kun film, der indeholder søgeteksten i titlen, bliver vist.
>- Listen konverteres til en rigtig liste og sendes til [[MVC#View|Viewet]] ([[HTML Struktur|HTML]]-siden) for at blive vist.