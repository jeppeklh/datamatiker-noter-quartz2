---
aliases:
  - DI
---

> [!tldr] Definition
> Et designmønster, der hjælper med at holde koden modulær, testbar og nem at udvide. Det gør det ved at overføre ansvaret for oprettelse og håndtering af afhængigheder fra klasser til en ekstern container, hvilket reducerer koblingen mellem komponenterne.

---

## Hvad er Dependency Injection?
- **Definition:** DI er en metode, hvor en klasse modtager sine nødvendige afhængigheder (såsom databaser, logger, services osv.) udefra i stedet for at instantiere dem internt.
- **Analogi:** Tænk på en bil, der ikke selv fremstiller sine dæk, men modtager dem færdige fra en fabrik.
- **Fordele:**
  - Reducerer koblingen mellem klasser.
  - Forbedrer testbarhed ved at muliggøre udskiftning med mock-implementeringer.
  - Øger fleksibilitet og vedligeholdelighed af koden.


---

## Dependency Injection i MVC
I [[MVC]] anvendes DI til at levere de nødvendige services til controllere og andre komponenter.

#### Eksempel på DI i ASP.NET Core MVC

1. **Definer et Interface og en Service:**
```csharp
public interface IGreetingService
{
	string GetGreeting();
}

public class GreetingService : IGreetingService
{
	public string GetGreeting()
	{
		return "Hello, World!";
	}
}
```

2. **Registrer Service i Startup.cs:**
```csharp
public class Startup
{
	public void ConfigureServices(IServiceCollection services)
	{
		services.AddControllersWithViews();
		services.AddScoped<IGreetingService, GreetingService>();
	}

	// Anden konfiguration...
}
```

3. **Brug Service i en Controller:**
```csharp
public class HomeController : Controller
{
	private readonly IGreetingService _greetingService;

	public HomeController(IGreetingService greetingService)
	{
		_greetingService = greetingService;
	}

	public IActionResult Index()
	{
		ViewBag.Greeting = _greetingService.GetGreeting();
		return View();
	}
}
```
- **Forklaring:**
  - **Registrering:** `services.AddScoped<IGreetingService, GreetingService>()` registrerer servicen med en scoped livscyklus, så der oprettes en ny instans per anmodning.
  - **Injection:** HomeController modtager `IGreetingService` via konstruktøren, hvilket muliggør udskiftning med andre implementeringer (f.eks. ved test).

---

## Dependency Injection i Blazor
[[Blazor Overview|Blazor]] understøtter også DI, hvilket gør det muligt at dele services mellem klient- og serverkomponenter.

### DI i Blazor Server/WebAssembly

I Blazor kan du registrere services i DI-containeren og derefter indsætte dem direkte i dine komponenter.

#### Eksempel på DI i en Blazor-applikation

1. **Opret en Service med Interface:**
```csharp
public interface IGreetingService
{
	string GetGreeting(string name);
}

public class GreetingService : IGreetingService
{
	public string GetGreeting(string name)
	{
		return $"Hello, {name}! Welcome to Blazor!";
	}
}
```

2. **Registrer Servicen i Startup.cs eller Program.cs:**
```csharp
public class Startup
{
	public void ConfigureServices(IServiceCollection services)
	{
		services.AddSingleton<IGreetingService, GreetingService>();
	}

	public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
	{
		app.UseRouting();
		app.UseEndpoints(endpoints =>
		{
			endpoints.MapBlazorHub();
			endpoints.MapFallbackToPage("/_Host");
		});
	}
}
```
- **Registrering:** `services.AddSingleton<IGreetingService, GreetingService>()` sikrer, at der kun oprettes én instans af `GreetingService` i hele applikationens levetid.

3. **Indsæt og Brug Servicen i en Blazor-Komponent:**
```razor
@page "/greet"
@inject IGreetingService GreetingService

<h3>Greeting</h3>
<p>@greetingMessage</p>

@code {
	private string greetingMessage;

	protected override void OnInitialized()
	{
		greetingMessage = GreetingService.GetGreeting("World");
	}
}
```
- **Forklaring:**
  - **@inject:** Bruges til at indsætte `IGreetingService` i komponenten.
  - **OnInitialized:** Komponentens initialiseringsmetode, hvor servicen kaldes for at hente en hilsen, der vises til brugeren.

---

## Opsummering
- **Dependency Injection** gør det muligt at holde koden løs koblet ved at overføre ansvaret for at oprette afhængigheder til en ekstern container.
- **I MVC:** DI hjælper med at levere nødvendige services til controllere, hvilket øger testbarhed og vedligeholdelse.
- **I Blazor:** DI muliggør deling af services mellem klient- og serverkomponenter, hvilket fremmer kodegenbrug og konsistens.

---

## Resourcer
- [Dependency Injektion Læringsobjekt (MVC)](https://scorm.itslearning.com/data/3289/C20150/ims_import_43/scormcontent/index.html#/lessons/08SZ6y2wtJzg6oNAUyevtSZGxDS4ORkq)
- [Dependency Injektion Læringsobjekt (Blazor)](https://scorm.itslearning.com/data/3289/C20150/ims_import_43/scormcontent/index.html#/lessons/yGlvEqvIFILy47jfHVEMbhUgYC-b0L8z)
- [Dependency Injektion LinkedIn Kursus](https://www.linkedin.com/learning/asp-dot-net-core-in-dot-net-6-dependency-injection/dependency-injection-overview?resume=false&u=57075649)
