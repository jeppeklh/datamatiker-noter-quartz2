> [!info] Grupper
En central funktion i [[SignalR]] er understøttelsen af **grupper**, som gør det muligt at organisere forbindelser og målrette beskeder til specifikke undersæt af klienter.

---
> [!tldr] Definition
  >En gruppe er en samling af forbindelser, identificeret ved et navn.  
 > - En klient kan tilhøre flere grupper.
  >- Grupper oprettes dynamisk, når den første klient tilføjes.
  >- Grupper fjernes automatisk, når den sidste klient forlader gruppen.

- **Kommandoer til gruppestyring:**
  - **Tilføj en forbindelse til en gruppe:**
    ```csharp
    await Groups.AddToGroupAsync(connectionId, "gruppenavn");
    ```
  
  - **Fjern en forbindelse fra en gruppe:**
```csharp
await Groups.RemoveFromGroupAsync(connectionId, "gruppenavn");
```
  
  - **Send besked til alle i en gruppe:**
```csharp
await Clients.Group("gruppenavn").SendAsync("beskedNavn", data);
```

---

## Persistens af Grupper
---
Som standard er gruppemedlemskaber i SignalR **ikke persistente**:
- Når en klient mister forbindelsen eller genstarter, går gruppemedlemskaber tabt.
- Ved servergenstart nulstilles alle gruppemedlemskaber.

### Muligheder for at implementere persistens:

1. **Manuel Tracking:**
   - Gem gruppemedlemskaber i en database.
   - Genopret medlemskaber, når klienten genopretter forbindelsen.

2. **SignalR Backplanes:**
   - Brug backplanes (f.eks. Redis, SQL Server eller Azure SignalR Service) for at understøtte skalering på tværs af servere.
   - Bemærk, at disse ikke gemmer medlemskaber ved servergenstart.

3. **Tilpasset Connection Mapping:**
   - Opret en in-memory mapping til at spore forbindelser og deres grupper (dog ikke persistent ved genstart).
   - Eksempel:
 ```csharp
 // In-memory mapping (ikke persistent)
 private static Dictionary<string, HashSet<string>> _userConnectionMap = new();
 private static Dictionary<string, HashSet<string>> _connectionGroupMap = new();

 public override async Task OnConnectedAsync() {
	 string userId = Context.User.Identity.Name;
	 string connectionId = Context.ConnectionId;
	 
	 // Tilføj forbindelse til bruger-mapping
	 if (!_userConnectionMap.ContainsKey(userId)) {
		 _userConnectionMap[userId] = new HashSet<string>();
	 }
	 _userConnectionMap[userId].Add(connectionId);
	 
	 // Genopret gruppemedlemskaber fra en database
	 var groups = await _databaseService.GetUserGroupsAsync(userId);
	 foreach (var group in groups) {
		 await Groups.AddToGroupAsync(connectionId, group);
		 // Opdater tracking
		 if (!_connectionGroupMap.ContainsKey(connectionId)) {
			 _connectionGroupMap[connectionId] = new HashSet<string>();
		 }
		 _connectionGroupMap[connectionId].Add(group);
	 }
 }
 ```



## Resourcer
---
- [SignalR LinkedIn Kursus (Groups)](https://www.linkedin.com/learning/learning-signalr-with-asp-dot-net-core/how-groups-work-in-signalr?resume=false&u=57075649)
- [SignalR Læringsobjekt (Grupper)](https://scorm.itslearning.com/data/3289/C20150/ims_import_42/scormcontent/index.html#/lessons/ihTc4kwKaHn_XlGEoxI1i9piWYiO3i80)
