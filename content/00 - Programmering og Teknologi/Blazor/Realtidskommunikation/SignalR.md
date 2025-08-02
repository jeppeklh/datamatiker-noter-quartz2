> [!tldr] Definition
> Et bibliotek udviklet af Microsoft, der muliggør realtidskommunikation mellem klient og server. 
>
> Ved at oprette vedvarende forbindelser gør SignalR det muligt for serveren at sende data direkte til klienter uden, at de selv skal anmode om opdateringer. Dette opnås gennem [[The Hub|hubs]], som forenkler tovejskommunikationen ved at lade både klienter og servere kalde hinandens metoder direkte.


- **Persistent Forbindelse:**  
  SignalR etablerer en konstant forbindelse mellem klienten og serveren, hvilket muliggør en tovejskommunikation. Dette betyder, at når en klient opretter forbindelse, kan både klient og server kalde hinandens metoder direkte.

- **Dynamisk Samspil:**  
  Når en klient opretter forbindelse til en hub, opstår et dynamisk samspil, hvor begge parter konstant kan opdatere hinanden med nye data.

- **Automatisk Protokolvalg:**  
  SignalR evaluerer automatisk de tilgængelige transportprotokoller og vælger den mest effektive. WebSockets foretrækkes grundet sin effektivitet, men hvis det ikke er tilgængeligt, falder SignalR tilbage på andre metoder som Server-Sent Events eller long polling.

- **Robusthed og Fallback:**  
  Ved forbindelsesafbrydelser aktiveres en indbygget fallback-strategi, som arbejder for at genetablere forbindelsen uden brugerindgriben.

---

## Implementering af SignalR i Projekter
Implementeringen af SignalR følger typisk disse trin:

1. **Opret [[The Hub|Hub]]-klassen:**  
   Definer en hub på serveren, som fungerer som kommunikationscenter.

2. **Konfigurer SignalR:**  
   Konfigurer SignalR i projektets startup-kode (f.eks. i `Startup.cs` eller `Program.cs`).

3. **Integrer Klientbiblioteket:**  
   Tilføj og konfigurer SignalR-klientbiblioteket i din webapplikation.

4. **Etabler Forbindelse til Hub:**  
   Klienten opretter en forbindelse til den definerede hub.

5. **Definer Klientmetoder:**  
   Opsæt klientmetoder, som kan modtage beskeder fra serveren.

6. **Kalder Servermetoder:**  
   Klienten kan nu kalde metoder på serveren, og omvendt.

---

## Resourcer
- [SignalR LinkedIn Kursus](https://www.linkedin.com/learning/learning-signalr-with-asp-dot-net-core/what-is-signalr?resume=false&u=57075649)
- [SignalR Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_42/scormcontent/index.html#/lessons/w1ZMNioiXENhGBGIdJI7D47eQlxSLLt-)