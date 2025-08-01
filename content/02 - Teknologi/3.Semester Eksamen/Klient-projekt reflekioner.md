### ✅ **Klient-projektet – Hvad bruges det til i jeres løsning?**

Klient-projektet (`GotorzProjectMain.Client`) bruges til at levere interaktive brugerflader, der kører direkte i browseren ved hjælp af Blazor WebAssembly.
 F.eks. kører chat-siden (`Chat.razor`) som en interaktiv komponent i browseren og kommunikerer med serveren via SignalR. Det indeholder også modeller og services, som skal bruges på klientsiden.

---

### ✅ **WebAssembly – Hvad er Blazor WebAssembly, og hvornår kører en komponent i browseren?**

Blazor WebAssembly (WASM) er en teknologi, der tillader .NET-kode at køre direkte i browseren uden behov for en server. 
En komponent kører i browseren, når den er rendere med `WebAssemblyRenderMode.Interactive`. Det gør, at komponenten kan reagere på brugerens input uden at skulle kalde serveren for hver handling – det giver en hurtig og responsiv brugeroplevelse.

---

### ✅ **Hybrid rendering – Hvad betyder det, at jeres løsning understøtter hybrid rendering?**

Hybrid rendering betyder, at jeres Blazor-applikation understøtter både server-side rendering (SSR) og client-side rendering (WASM). Det gøres gennem `AddInteractiveServerRenderMode()` og `AddInteractiveWebAssemblyRenderMode()`, som gør det muligt at vælge renderingsmetode pr. komponent. Det giver fleksibilitet – nogle komponenter kan køre på serveren, mens andre kan køre i browseren, afhængigt af behov.

---

### ✅ **SignalR og Chat – Hvordan fungerer chat-komponenten i browseren?**

Chat-komponenten (`Chat.razor`) er en Blazor WebAssembly-side, der kører i browseren. Den bruger SignalR til at oprette en WebSocket-forbindelse til en chat-hub på serveren (`/chathub`). Brugeren kan sende beskeder, som straks vises i UI'et og samtidig sendes til andre klienter via SignalR, som håndterer realtidsopdatering af beskeder.

---

### ✅ **Authentication – Hvad gør `PersistentAuthenticationStateProvider`? Bliver den brugt?**

`PersistentAuthenticationStateProvider` er en klient-side AuthenticationStateProvider, der forsøger at læse brugerens oplysninger fra en komponent-tilstand (`PersistentComponentState`), som blev genereret af serveren ved initial load. Den skaber `Claims`-data, der kan bruges i klientkomponenter.  
**Men**: den bliver **kun brugt**, hvis komponenterne aktivt bruger `[CascadingParameter] AuthenticationState` eller `AuthorizeView`. I jeres projekt bruges Blazor Identity på serversiden, så denne provider er **sandsynligvis ikke aktivt brugt** medmindre I har koblet den eksplicit på UI'et.

---

### ✅ **Arkitektur – Hvad ville ske, hvis I fjernede klient-projektet?**

Hvis klient-projektet blev fjernet, ville det ikke længere være muligt at køre komponenter interaktivt i browseren via WebAssembly. 
Vi ville være begrænset til ren server-side Blazor. 

Det betyder bl.a., at komponenter som `Chat.razor` ikke kunne fungere uden fuld sideopdatering eller konstant kommunikation med serveren – hvilket ville påvirke brugeroplevelsen negativt i realtidssituationer.

---

### ✅ **Adskillelse – Hvorfor ligger login og autentifikation på serveren og ikke i klient-projektet?**

Login og autentifikation ligger på serveren, fordi serveren har adgang til databasen og kan validere brugeroplysninger sikkert. Det giver mulighed for at bruge Blazor Identity, som håndterer login, logout, cookies og sessioner korrekt. Klienten er usikker og kan manipuleres, så derfor håndteres autentifikation **aldrig** kun på klientsiden – klienten kan højst få læseadgang til brugerens oplysninger for at vise UI-tilpasning.


### 🔹 **Formål**

Klient-projektet `GotorzProjectMain.Client` er et **Blazor WebAssembly (WASM)** projekt. Det bruges til at køre interaktive brugergrænseflader direkte i browseren. Det er nødvendigt i jeres løsning, fordi I har valgt at bruge **hybrid rendering** via Blazor, hvor nogle komponenter kan køres enten på serveren eller i browseren.

### 🔹 **Konkrete ting det bruges til**

1. **Interaktiv UI i browseren**  
    Sider som `Chat.razor` kører i browseren og interagerer direkte med brugeren uden at gå via serveren for hver klik. Den bruger f.eks. SignalR til live-chat.
    
2. **Chat-model til UI**  
    `ChatMessage.cs` definerer dataobjekter, som bliver brugt i `Chat.razor` til at vise beskeder.
    
3. **Hybrid rendering (Blazor United)**  
    Jeres konfiguration i `Program.cs` og `app.MapRazorComponents<App>()` understøtter både:
    
    - `AddInteractiveServerRenderMode()` – kørsel på serveren
        
    - `AddInteractiveWebAssemblyRenderMode()` – kørsel i browseren  
        Dette kræver, at klient-projektet eksisterer, så det kan levere de nødvendige assemblies og komponenter til browseren.
        
4. **(Potentiel) Klientside AuthenticationStateProvider**  
    I har en `PersistentAuthenticationStateProvider`, som kan bruges til at vise information om den loggede bruger på klientsiden.  
    Den bliver registreret i `Program.cs`, men bliver **kun brugt**, hvis komponenter i klienten efterspørger autentificeringsstatus (f.eks. via `AuthorizeView`, `[CascadingParameter] AuthenticationState` osv.).
    

---

## ❓ **Hvorfor er der så få filer i klient-projektet?**

Fordi jeres løsning **primært håndterer logik, authentication og data på serversiden**. Klient-projektet behøver kun indeholde:

- Komponenter, der skal være interaktive i browseren (som `Chat.razor`)
    
- De modeller og services, der skal bruges i browseren (som `ChatMessage`, `UserInfo`)
    

Det er altså **intentionelt let**, og det er helt normalt i en hybrid Blazor-løsning.

---

## 📌 **Er klient-projektet nødvendigt?**

**Ja**, det er nødvendigt fordi:

- Uden det ville I ikke kunne køre komponenter i browseren via WebAssembly.
    
- Det indeholder koden, der bruges af `AddInteractiveWebAssemblyRenderMode()`.
    

Hvis I fjernede det, kunne I kun køre Blazor-server – ikke interaktive WASM-komponenter i browseren.