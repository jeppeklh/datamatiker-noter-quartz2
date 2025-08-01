
Realtidskommunikation gør det muligt for klienter (f.eks. webbrowsere) at modtage opdateringer med det samme, uden at brugeren manuelt skal anmode om data. Nøglepunkterne er:

- **Automatisk opdatering:** Så snart data ændres på serveren, modtager klienten opdateringen med det samme.
- **Tovejskommunikation:** Både klienten og serveren kan sende beskeder, uden at klienten behøver at spørge.
- **Fleksibilitet:** Serveren kan sende beskeder til alle tilsluttede klienter (f.eks. offentlige meddelelser) eller til individuelle klienter (f.eks. private beskeder).

> [!example] Eksempel
>- **Email-klienter:** Gmail modtager nye emails automatisk, uden at brugeren skal opdatere siden.
>- **Børsapplikationer:** Aktiekurser opdateres løbende, så brugeren altid ser de seneste tal.


## Dataoverførselsmetoder: Pull vs. Push
---
I webudvikling skelner vi mellem to primære metoder til dataoverførsel:

### Pull-teknologi
- **Definition:** Klienten anmoder aktivt om data fra serveren.
- **Sammenligning:** Det er som at banke på døren for at få information.
- **Anvendelse:** Traditionelle hjemmesider, hvor siden genindlæses ved hver ny forespørgsel.

### Push-teknologi
- **Definition:** Serveren sender data til klienten, uden at klienten anmoder om det.
- **Sammenligning:** Det svarer til at modtage en sms – beskeden kommer ind, så snart den er klar.
- **Anvendelse:** Chatapplikationer, livestreaming, sociale mediers notifikationer og online spil, hvor øjeblikkelig information er afgørende.



## Introduktion til SignalR
----
[[SignalR]] er en central teknologi for at implementere realtidsfunktionalitet i .NET Core-applikationer, inklusive Blazor. Her er nogle vigtige punkter:

- **Formål:** Gør det muligt for serveren at "pushe" data til klienten, så snart dataene er tilgængelige.
- **Underliggende teknologi:** Benytter Remote Procedure Call (RPC), hvor serveren kan kalde funktioner direkte på klienten.
- **Platforme:** SignalR-klient-SDK’er findes til JavaScript, .NET (C#, F# og Visual Basic) og Java, hvilket gør det nemt at integrere med en bred vifte af platforme – fra webapps til mobile enheder.
- **Hosting:** Kan hostes på egne servere eller som en fuldt administreret tjeneste på Azure Cloud Platform.
- **Ydeevne:** Designet til at levere høj ydeevne med minimal forsinkelse, hvilket er essentielt for applikationer, der kræver de seneste data øjeblikkeligt.

> [!example] Eksempel
>- **Chatapplikationer:** Brugere modtager nye beskeder i realtid.
>- **Spil:** Spillere oplever hurtige opdateringer af spiltilstande og handlinger.
>- **IoT:** Alarmer fra IoT-enheder (fx bevægelses- eller temperatursensorer) sendes med det samme til brugerne.
>- **Aktiekurser:** Markedsdata opdateres løbende til de tilsluttede klienter.



## Realtidskommunikation i Blazor
---
Når du udvikler med Blazor, kan du implementere realtidsfunktionalitet ved at integrere SignalR. Dette åbner op for følgende muligheder:

- **Live dataopdateringer:** Brugere får øjeblikkelige opdateringer, fx i dashboards eller interaktive brugergrænseflader.
- **Interaktive brugeroplevelser:** Applikationen kan reagere direkte på ændringer i data, hvilket giver en mere dynamisk og engagerende oplevelse.
- **Integration med andre systemer:** Realtidsdata kan også kombineres med IoT-enheder, sociale medieplatforme eller andre back-end systemer.

### Eksempel i Blazor med SignalR
---
```csharp
// Startup.cs eller Program.cs
public void ConfigureServices(IServiceCollection services)
{
    services.AddSignalR();
    // Tilføj øvrige services, f.eks. Razor Pages eller Blazor Server
}

public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    // Konfiguration af middleware
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapBlazorHub();
        endpoints.MapHub<MyHub>("/myhub");
        endpoints.MapFallbackToPage("/_Host");
    });
}

// Eksempel på en simpel Hub-klasse
public class MyHub : Hub
{
    public async Task SendMessage(string user, string message)
    {
        await Clients.All.SendAsync("ReceiveMessage", user, message);
    }
}
```
- **SignalR registreres** i `ConfigureServices`.
- **Hub'en** (`MyHub`) definerer en metode, der sender beskeder til alle tilsluttede klienter.
- Klienterne kan forbinde til denne hub og modtage beskeder, så snart de bliver sendt fra serveren.

![[SignalR.png]]

## Resourcer
---
- [Blazor - SignalR Læringobjet](https://scorm.itslearning.com/data/3289/C20150/ims_import_42/scormcontent/index.html#/lessons/255OK9oFlX5WtX7XlJ8iBWklihRRCOwG)
- [SignalR Youtube Video](https://www.youtube.com/watch?v=LEImpa77irI&ab_channel=tutorialsEU-C%23)
- [SignalR LinkedIn Kursus](https://www.linkedin.com/learning/learning-signalr-with-asp-dot-net-core/what-is-signalr?u=57075649)