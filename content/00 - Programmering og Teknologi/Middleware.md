> [!tldr] Definition
> En softwarekomponent, der fungerer som en bro mellem applikationer, lag eller systemer. > Dets primære funktion er at lette kommunikation og dataudveksling, samtidig med at den skjuler kompleksiteten i den underliggende infrastruktur.

---

## Funktioner og Formål
Middleware udfører flere kerneopgaver:
- **Kommunikation:** Koordinerer dataudveksling mellem distribuerede systemer (f.eks. via API’er eller messaging-køer).
- **Dataomformning:** Oversætter dataformater (f.eks. fra XML til JSON).
- **Sikkerhed:** Håndterer autentificering, autorisation og kryptering.
- **Skalerbarhed:** Fordeler arbejdsbyrder og understøtter elastiske cloud-miljøer.
- **Fejlhåndtering:** Genoptager afbrudte transaktioner og sikrer synkronisering ved netværksproblemer.

---

## Middleware i MVC
I ASP.NET Core anvendes middleware til at behandle HTTP-anmodninger og -svar. Det fungerer som et rør, hvor hver komponent kan:
- Behandle indkommende anmodninger.
- Videregive anmodningen til næste middleware.
- Behandle udgående svar.

### Opsætning i MVC-applikationer
- **Placering:** Middleware konfigureres i `Startup.cs` (eller `Program.cs` i nyere versioner).
- **Anvendelser:** Autentificering, logning, fejlhåndtering og omprioritering.
- **Flow:** Middleware kører *før* controller-handlinger, hvilket giver mulighed for at inspicere og modificere både anmodninger og svar.

---

## Eksempel på Custom Middleware
### Middleware Klasse
```csharp
public class CustomMiddleware
{
    private readonly RequestDelegate _next;
    
    public CustomMiddleware(RequestDelegate next)
    {
        _next = next;
    }
    
    public async Task InvokeAsync(HttpContext context)
    {
        // Kode der kører før det næste middleware
        Console.WriteLine($"Forespørgsel modtaget til {context.Request.Path}");
        
        // Kalder det næste middleware i pipelinen
        await _next(context);
        
        // Kode der kører efter det næste middleware
        Console.WriteLine("Svar sendt til klienten");
    }
}
```

---

### Registrering i Startup.cs
```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    // Tilføjelse af custom middleware til pipelinen
    app.UseMiddleware<CustomMiddleware>();
    
    // Standard middleware-komponenter
    app.UseRouting();
    app.UseAuthorization();
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapControllerRoute(
            name: "default",
            pattern: "{controller=Home}/{action=Index}/{id?}");
    });
}
```
### Forklaring af Eksemplet

- **`RequestDelegate _next`:** Reference til næste middleware i kæden.
- **Konstruktør:** Gemmer referencen til næste middleware.
- **`InvokeAsync(HttpContext context)`:**
    - Udfører kode før anmodningen sendes videre.
    - Kalder næste middleware med `await _next(context)`.
    - Udfører kode efter at det næste middleware har behandlet anmodningen.

---

## Middleware i Blazor
Selvom Blazor er et UI-framework, anvender **Blazor Server** stadig middleware til at håndtere SignalR-forbindelser. Der er dog forskelle mellem Blazor Server og Blazor WebAssembly:

- **Blazor Server:**
    - Komponenter hostes på serveren.
    - Kommunikationen til browseren sker via SignalR.
    - Middleware bruges til autentificering og HTTP-kommunikation.

- **Blazor WebAssembly:**
    - Kører direkte i browseren og bruger ikke middleware på samme måde.

### Typisk Middleware Pipeline for en .NET Core-applikation (MVC & Blazor)
```csharp
app.UseExceptionHandler("/Error");   // Håndterer undtagelser
app.UseStaticFiles();                // Serverer statiske filer (CSS, JS, billeder)
app.UseRouting();                    // Aktiverer routing
app.UseAuthentication();             // Håndterer autentificering
app.UseAuthorization();              // Håndterer autorisering
app.UseEndpoints(endpoints =>
{
    endpoints.MapBlazorHub();         // Opsætter SignalR-hubben til Blazor
    endpoints.MapControllers();       // Registrerer controller-endpoints
    endpoints.MapFallbackToPage("/_Host"); // Fallback-side for Blazor Server
});
```

### Gennemgang af Pipeline-konfigurationen

- **`app.UseExceptionHandler("/Error")`:** Omdirigerer ved undtagelser.
- **`app.UseStaticFiles()`:** Muliggør servering af statiske filer.
- **`app.UseRouting()`:** Nødvendigt for endpoint-routing.
- **`app.UseAuthentication()` og `app.UseAuthorization()`:** Sikrer korrekt håndtering af brugersikkerhed.
- **`app.UseEndpoints()`:** Konfigurerer specifikke mappings for Blazor, controllers og fallback-sider.

---

## Opsummering
Middleware spiller en central rolle i at lette integrationen mellem forskellige systemer og teknologier ved at:

- Abstrahere kompleksiteten i netværks- og kommunikationslag.
- Muliggøre fleksibel konfiguration af request- og responsehåndtering.
- Understøtte både MVC og Blazor med specialiserede pipelines til håndtering af HTTP-anmodninger og -svar.

---

## Resourcer
- [Middleware Læringsobjekt (MVC)](https://scorm.itslearning.com/data/3289/C20150/ims_import_43/scormcontent/index.html#/lessons/Foj6ILDTHJtYU-XYT1Fuz-UdWaH6AZP6)
- [Middleware Læringsobjekt (Blazor)](https://scorm.itslearning.com/data/3289/C20150/ims_import_43/scormcontent/index.html#/lessons/d81MkqT6Ye8GcpyV-kLrdiL0nPECodD0)
- [Middleware LinkedIn Kursus](https://www.linkedin.com/learning/asp-dot-net-core-middleware/welcome?u=57075649)