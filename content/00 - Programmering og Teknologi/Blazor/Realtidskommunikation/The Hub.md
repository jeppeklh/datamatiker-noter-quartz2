
En SignalR Hub er hjertet i realtidskommunikationen:

- **Abstraktion af Kompleksitet:**  
  Ved hjælp af Remote Procedure Calls (RPC) kan serveren og klienten kalde hinandens metoder uden at skulle håndtere den underliggende kommunikation (f.eks. WebSockets eller HTTP).

- **Håndtering af Forbindelser:**  
  Hubs sporer automatisk tilsluttede klienter, grupper og livscyklus-hændelser, såsom tilslutning og frakobling.

- **Broadcast og Gruppemeddelelser:**  
  Gør det muligt at sende beskeder til alle klienter, udvalgte klienter eller bestemte grupper. Dette er især nyttigt i scenarier som chatapplikationer, hvor man vil sende beskeder til en bestemt gruppe brugere.

### Eksempel på en simpel ChatHub

```csharp
public class ChatHub : Hub 
{
    public async Task SendMessage(string bruger, string besked)
    {
        // Sender beskeden til alle tilsluttede klienter
        await Clients.All.SendAsync("ModtagBesked", bruger, besked);
    }
}
```

---

## Praktisk Eksempel – Implementering af en Chatklient
### Server-side Opsætning

**Registrering i Startup:**
```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSignalR();
    // Andre services (f.eks. Razor Pages eller Blazor Server)
}

public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapHub<ChatHub>("/chatHub");
        // Andre endpoints
    });
}
```

### Klient-side Kode
```csharp
using Microsoft.AspNetCore.SignalR.Client;

// Opretter forbindelse til ChatHub
var connection = new HubConnectionBuilder()
    .WithUrl("https://din-server-url/chatHub")
    .Build();

// Lyt til "ModtagBesked"-metoden
connection.On<string, string>("ModtagBesked", (bruger, besked) => 
{
    Console.WriteLine($"{bruger}: {besked}");
});

try
{
    // Starter forbindelsen
    await connection.StartAsync();
    
    // Sender en besked til serveren
    await connection.InvokeAsync("SendMessage", "Alice", "Hej verden!");
}
catch (Exception ex)
{
    Console.WriteLine($"Fejl: {ex.Message}");
}
```

### Gruppemeddelelser og Livscyklus-håndtering

- **Tilføj en klient til en [[SignalR Grupper|gruppe]]:**
```csharp
await Groups.AddToGroupAsync(Context.ConnectionId, "GruppeA");
```

- Send besked til en gruppe:
```csharp
await Clients.Group("GruppeA").SendAsync("ModtagBesked", "Hej GruppeA!");
```

- **Livscyklus-metoder:**  
	Du kan overskrive `OnConnectedAsync()` og `OnDisconnectedAsync()` for at tilpasse logik ved tilslutning og frakobling af klienter.
	Det kune være en Velkommen besked til alle klienter der lige er connected.

---

## Resourcer
- [SignalR Læringsobjekt (The hub)](https://scorm.itslearning.com/data/3289/C20150/ims_import_42/scormcontent/index.html#/lessons/bz461eD2LAc3_YeCh5pJNLHN5hI_ZyoV)
- [Basic Chat with SignalR LinkedIn Kursus eksempel](https://www.linkedin.com/learning/learning-signalr-with-asp-dot-net-core/add-a-signalr-hub?autoSkip=true&resume=false&u=57075649)
- 