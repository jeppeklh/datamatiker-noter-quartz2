### Introduktion
Jeg vil gennemgå vores sekvensdiagram for vores flysøgning.  
Det viser, hvordan en brugerinteraktion starter en kæde af kald fra UI og frontend, gennem backend og videre til en ekstern API.

Vi laver et direkte API-kald fra vores Serverprojekt til den eksterne API. 
Det er en enkel løsning, og vi er bevidste om, at det både har fordele og ulemper.

---

### Bruger starter søgningen
Det hele begynder, når brugeren klikker på **'Search'** i brugergrænsefladen.  

SKIFT
Det kalder metoden `SearchAsync()` i vores `FlightSearch Component`, som er ansvarlig for datahentningen.
Metoden bliver kaldt med de input, brugeren har indtastet i UI’en:

- Hvor vi flyver fra (fra-IATA)
    
- Hvor vi flyver til (til-IATA)
    
- Dato
    
- Antal børn og voksne

---

### Kald til ekstern API
I `FlightService` samles alle parametre, og vi bygger en query-url.  

SKIFT
Herefter laver vi et GET-kald med en `HttpClient` til **API'en**, som returnerer data i JSON-format – altså data om flyruterne.


SKIFT

---

### Første møde med DTO’er
Vi deserialiserer JSON-svaret til et `FlightResponseDTO` objekt.  

Her bruger vi **DTO’er (Data Transfer Objects)** for at holde data, vi får fra API’et, adskilt fra vores egne modelklasser.

DTO’er fungerer som en slags buffer, hvor vi kan strukturere og validere API-data **før vi mapper dem videre til vores egne modeller**.


**FlightResponseDTO** indeholder alle data fra API'et. 
Det **matcher** præcist **API**'ets **JSON**-**struktur**, så vi nemt kan **deserialisere** dataene **uden** at skulle lave **kompleks** **mapping** først.

Den indeholder to lister med flyruter:
- **BestFlights** (prioriterede ruter)
    
- **OtherFlights** (øvrige ruter)
    
Begge lister består af **FlightRouteDTO-objekter**, hvor hver rute selv indeholder:
1. En liste af **FlightLegDTO'er** (de enkelte flysegmenter)
    
2. En liste af **LayoverDTO'er** (eventuelle mellemlandinger)
    
3. Den samlede **pris** for ruten



SKIFT

---

### Sammenlægning af data
Som sagt opdeler  API'en flyruterne i `BestFlights` og `OtherFlights`, ud fra pris og rejsetid.  
Men vi ønsker at vise **alle** ruter – ikke filtrere dem på forhånd – så vi **kombinerer de to lister til én samlet liste** af flyruter.


SKIFT

---

### Mapping fra DTO’er til modeller
Vi looper derefter over hver `FlightRouteDTO` og **mapper dataene til vores modelklasser**:

- Hver `FlightLegDTO` bliver til et `Flight`-objekt
SKIFT
- Hver `LayoverDTO` bliver til et `Layover`-objekt
SKIFT
- Til sidst samler vi det hele i en `FlightRoute`, der indeholder segmenter, layovers og pris
    

DTO’erne bliver altså brugt **udelukkende som input** fra API'en– vi persisterer dem ikke.

**Det giver os noget fleksibilitet** 
Hvis API’et ændres, skal vi **kun justere DTO’erne og mappings**, ikke resten af vores system.

---

### Resultater og rendering
Til sidst returnerer `FlightService` en liste af `FlightRoute`-objekter til `FlightSearch Component`, som viser ruterne i en dropdown – med informationer som mellemlandinger, flyselskaber og pris.
