
> [!note] Info
SignalR tilbyder flere metoder til at identificere og håndtere brugere, hvilket gør det muligt at sende beskeder præcist til de rette modtagere og spore brugere på tværs af forbindelser.

## Identifikation af Brugere
---
### Connection ID
- **Unik Identifikator:**  
  Hver bruger får et unikt Connection ID, når de opretter forbindelse.
- **Brug:**  
  Dette ID bruges til at sende beskeder til specifikke forbindelser.
- **Begrænsning:**  
  Connection ID'et ændres, hvis brugeren mister forbindelsen og genopretter den.

### User Identity
- **Autentificerede Brugere:**  
  Ved at knytte brugerne til ASP.NET Identity kan du spore dem på tværs af forbindelser.
- **Brugernavn:**  
  Brug `Context.User.Identity.Name` for at hente det autentificerede brugernavn.
  


## Grupper og Persistente Forbindelser
---
### Grupper
- **Organisering:**  
  Brugere kan tilføjes til grupper for nemmere håndtering, hvilket muliggør samtidig beskedudsendelse til flere brugere.
- **Eksempel:**  
```csharp
await Groups.AddToGroupAsync(Context.ConnectionId, "AdminGroup");
```

### Persistente Forbindelser
- **Genoptagelse af Sessioner:**  
    SignalR tilbyder mekanismer til at gemme brugerinformation, så sessioner kan genoptages, når forbindelsen genetableres.


## Eksempel: Brugerhåndtering i en ChatHub
---
```csharp
public class ChatHub : Hub
{
    public override async Task OnConnectedAsync()
    {
        // Hent brugerens navn via ASP.NET Identity
        var userName = Context.User.Identity.Name;
        
        // Tilføj brugeren til en gruppe baseret på deres rolle
        if (Context.User.IsInRole("Admin"))
        {
            await Groups.AddToGroupAsync(Context.ConnectionId, "Administrators");
        }
        
        // Informer alle klienter om, at en bruger har oprettet forbindelse
        await Clients.All.SendAsync("UserConnected", userName);
        
        await base.OnConnectedAsync();
    }
}
```

## Resourcer
---
- [SignalR Læringsobjekt (Brugere)](https://scorm.itslearning.com/data/3289/C20150/ims_import_42/scormcontent/index.html#/lessons/AaHIbxOZIEeb61ZxGWNmOpdNgZQTuseN)
- [SignalR LinkedIn Kursus (Users)](https://www.linkedin.com/learning/learning-signalr-with-asp-dot-net-core/users-and-authentication?resume=false&u=57075649)
