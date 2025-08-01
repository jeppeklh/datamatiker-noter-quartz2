> [!tldr] Definition
Fejl-logning er en essentiel del af enhver applikationsudvikling, da det hjælper med at identificere, diagnosticere og rette fejl, der opstår under en Blazor-applikations levetid. En effektiv logningsstrategi forbedrer applikationens robusthed og pålidelighed.



## Metoder til Fejl-logning
---
### 1. Try-Catch Blokke
---
Ved at anvende try-catch blokke i dine komponenter kan du fange undtagelser og logge fejlmeddelelser, hvilket gør det nemmere at diagnosticere problemer.

**Eksempel:**
```razor
@page "/example"
@inject ILogger<ExampleComponent> Logger

<h3>Try-Catch Example</h3>

@code {
    protected override async Task OnInitializedAsync()
    {
        try
        {
            // Simuler en fejl
            throw new InvalidOperationException("Dette er en testfejl.");
        }
        catch (Exception ex)
        {
            Logger.LogError(ex, "En fejl opstod under initialisering.");
        }
    }
}
```

### 2. Dependency Injection af Logging
---
Blazor udnytter dependency injection til at centralisere og standardisere logning på tværs af applikationen. Du kan konfigurere logningstjenester i **Program.cs** (eller Startup.cs) og herefter injicere `ILogger<T>` i dine komponenter.

**Konfiguration i Program.cs:**
```csharp
var builder = WebApplication.CreateBuilder(args);

// Konfigurer logging (f.eks. til konsollen)
builder.Services.AddLogging(configure => configure.AddConsole());

// Tilføj nødvendige Blazor-tjenester
builder.Services.AddRazorPages();
builder.Services.AddServerSideBlazor();

var app = builder.Build();

app.UseRouting();

app.UseEndpoints(endpoints =>
{
    endpoints.MapBlazorHub();
    endpoints.MapFallbackToPage("/_Host");
});

app.Run();
```

Eksempel i en komponent:
```razor
@page "/example"
@inject ILogger<ExampleComponent> Logger

<h3>Dependency Injection Example</h3>

@code {
    protected override void OnInitialized()
    {
        Logger.LogInformation("Komponenten er blevet initialiseret.");
    }
}
```

### 3. Integration med Logging Frameworks (f.eks. Serilog)
---
For udvidet logningsfunktionalitet kan du integrere populære logging frameworks som Serilog, der tilbyder avancerede konfigurationsmuligheder og fleksibelt logningsoutput.

**Eksempel med Serilog i Program.cs:**
```csharp
using Serilog;

Log.Logger = new LoggerConfiguration()
    .WriteTo.Console()
    .CreateLogger();

try
{
    Log.Information("Applikationen starter.");

    var builder = WebApplication.CreateBuilder(args);

    // Erstat den indbyggede logging med Serilog
    builder.Host.UseSerilog();

    builder.Services.AddRazorPages();
    builder.Services.AddServerSideBlazor();

    var app = builder.Build();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapBlazorHub();
        endpoints.MapFallbackToPage("/_Host");
    });

    app.Run();
}
catch (Exception ex)
{
    Log.Fatal(ex, "Applikationen blev stoppet uventet.");
}
finally
{
    Log.CloseAndFlush();
}
```

Eksempel i en komponent med Serilog:
```razor
@page "/example"
@inject ILogger<ExampleComponent> Logger

<h3>Serilog Example</h3>

@code {
    protected override void OnInitialized()
    {
        Logger.LogInformation("Komponenten er blevet initialiseret med Serilog.");
    }
}
```

## Opsummering
---
- **Try-Catch Blokke:** Bruges til at fange og logge fejl direkte i komponenterne, så du kan reagere på uventede hændelser.
- **Dependency Injection:** Gør det nemt at anvende logging på tværs af applikationen ved at injicere `ILogger<T>` i dine komponenter.
- **Logging Frameworks:** Ved at integrere frameworks som Serilog kan du udvide logningsmulighederne, tilpasse logoutput og dirigere logs til forskellige destinationer (f.eks. konsol, filer, databaser).

## Resourcer
---
- [Blazor WebAssembly Læringsobjekt (Fejl-logning)](https://scorm.itslearning.com/data/3289/C20150/ims_import_38/scormcontent/index.html#/lessons/PQMcPpO52flncHmYIiRrRc7StWj7566o)
- [Blazor WebAssembly LinkedIn Kursus (Logging and Error Handling)](https://www.linkedin.com/learning/blazor-webassembly-foundational-skills/how-logging-works-in-blazor?resume=false&u=57075649)
