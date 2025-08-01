### **Arkitektur og Design**

**Hvordan er ansvarsfordelingen mellem `FlightSearch Component`, `FlightService` og `HttpClient`?**

- `FlightSearch Component` står for UI og brugerinteraktionen. Den indsamler input (fra, til, dato, passagerantal) og kalder `FlightService`.
    
- `FlightService` håndterer al forretningslogik, såsom at kalde API’et, deserialisere data og mappe DTO’er til domænemodeller.
    
- `HttpClient` håndterer det konkrete HTTP-kald til SerpAPI. Den er ansvarlig for at hente rå JSON-data, ikke at tolke eller validere dem.
    

**Hvorfor har du valgt at bruge DTO-klasser? Hvad er fordelene?**  
DTO’er (Data Transfer Objects) adskiller den eksterne API-struktur fra applikationens interne domænemodeller. Fordelene er:

- Du kan ændre dine domænemodeller uden at påvirke eksterne API-kald.
    
- DTO’er gør det nemt at validere og konvertere data, før det bruges i applikationen.
    
- Det reducerer afhængighed på 3. parts datastrukturer, hvilket giver bedre vedligeholdelse og testbarhed.
    

---

### **Asynkronitet og Performance**

**Hvad sker der, hvis SerpAPI er langsom? Hvordan håndteres det?**

- `HttpClient.GetFromJsonAsync` er asynkron og blokerer ikke UI-threaden.
    
- Hvis kaldet er langsomt, vises typisk en loading-indikator (i UI), og brugeren kan ikke interagere, før svaret kommer.
    
- Der bør også sættes en timeout på `HttpClient`, og evt. retries eller fallback-logik kan implementeres.
    

**Kan man optimere loop’et, der genererer `FlightRoute` objekter?**

- Ja, hvis antallet af ruter er stort, kan man overveje:
    
    - Parallelisering (fx via `Parallel.ForEach`) – med forbehold for tråd-sikkerhed.
        
    - Caching eller batch-behandling, hvis mange ruter genbruger samme data (som lufthavne).
        
    - Lazy evaluation, hvis kun en delmængde af resultaterne vises ad gangen.
        

---

### **Fejlhåndtering**

**Hvordan håndterer du fejl i JSON-deserialisering?**

- `GetFromJsonAsync` kan kaste undtagelser ved forkert JSON eller inkompatible typer.
    
- Dette bør fanges med `try-catch`, og der kan logges fejl og vises en passende fejlmeddelelse til brugeren.
    
- Alternativt kan man bruge `System.Text.Json` manuelt og validere trinvis.
    

**Hvad sker der, hvis SerpAPI svarer med en tom liste?**

- Tjenesten vil stadig forsøge at oprette en tom liste af `FlightRouteDTO`.
    
- UI’et bør vise en besked som “Ingen flyvninger fundet” i stedet for dropdown med ruter.
    
- Der bør skelnes mellem “tomt resultat” og “fejl”.
    

---

### **DTO og Domænemodeller**

**Hvorfor adskiller du DTO’er og domænemodeller som `Flight`, `Layover`, `FlightRoute`?**

- DTO’er repræsenterer data i den form de kommer fra API’et.
    
- Modelklasser bruges internt og kan være optimeret til forretningslogik og UI (f.eks. indeholder `FlightRoute` totalpris og listede segmenter).
    
- Det giver fleksibilitet og isolering mellem eksterne og interne ændringer.
    

**Hvordan mapper du fra `FlightRouteDTO` til `FlightRoute`?**

- For hver `FlightRouteDTO` hentes dens `FlightLegDTOs` og `LayoverDTOs`.
    
- Disse konverteres til `Flight` og `Layover` instanser.
    
- Til sidst bruges disse til at konstruere en `FlightRoute`, f.eks. med en factory-metode eller mapping-funktion.
    

---

### **UI/UX Overvejelser**

**Hvornår opdateres UI’et – og hvordan sikrer du, at det ikke fryser?**

- UI’et opdateres, når `SearchAsync` returnerer resultaterne.
    
- Blazor bruger async/await og kører ikke langvarige operationer på UI-threaden.
    
- Eventuelle visninger (dropdown, liste osv.) bindes til en `List<FlightRoute>`, som opdateres reaktivt.
    

**Hvordan håndterer du loading state og fejlvisning i `FlightSearch Component`?**

- Komponentet bør bruge en `bool IsLoading` og `string ErrorMessage`.
    
- Når søgningen starter sættes `IsLoading = true`, og når svaret kommer, sættes den til false.
    
- Ved fejl vises `ErrorMessage` med en brugervenlig besked og evt. mulighed for retry.