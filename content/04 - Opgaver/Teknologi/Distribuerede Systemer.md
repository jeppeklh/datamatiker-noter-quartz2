  
## Opgave 1 -Opstarts opgaver
---
1. Find tre eksempler på distribuerede systemer i din hverdag og beskriv deres funktion.

- **Cloud Storage Services (f.eks. Google Drive, Dropbox, iCloud)** 
	- **Funktion:** Disse systemer gemmer og synkroniserer brugerdata (filer, fotos, dokumenter) på flere servere i et globalt netværk. Det sikrer, at data er tilgængelige fra enhver enhed og beskytter mod tab via replikering og fejltolerance.
	
- **Online Streaming Services (f.eks. Netflix, YouTube)**
	- **Funktion:** Streamingplatforme leverer video- og lydindhold til millioner af brugere samtidig. Ved hjælp af distribuerede Content Delivery Networks (CDN) caches indhold på servere tæt på brugerne, hvilket reducerer latency og forbedrer afspilningskvaliteten.

- **Online Banking og Betalingssystemer (f.eks. netbank, MobilePay)**
	- **Funktion:** Disse systemer håndterer finansielle transaktioner og giver brugerne adgang til kontooplysninger, betalinger og overførsler. De benytter distribuerede databaser og servere for at sikre høj tilgængelighed, sikkerhed og realtidsopdatering af data.


2. Tegn en model af en Client-Server, P2P og Microservices arkitektur og identificer fordele/ulemper.

3. Diskutér fordele og ulemper ved synkron og asynkron kommunikation.

**Synkron kommunikation:**
- **Fordele:**
    - Enkel implementering og fejlfinding, da kaldet blokerer og svar gives med det samme
    - Forudsigelig rækkefølge af operationer, hvilket gør debugging og test nemmere
    
- **Ulemper:**
    - Blokerende opkald kan føre til flaskehalse, når systemet venter på svar
    - Dårligere ydeevne under høje belastninger, da alle anmodninger skal behandles sekventielt

**Asynkron kommunikation:**
- **Fordele:**
    - Ikke-blokerende, hvilket gør det muligt at håndtere mange anmodninger parallelt
    - Bedre udnyttelse af ressourcer og højere throughput under belastning

- **Ulemper:**
    - Komplekst fejlhåndterings- og kontrolflow, da svar ikke kommer med det samme
    - Eventuel kompleksitet i at sikre, at alle meddelelser bliver behandlet korrekt og i den rigtige rækkefølge (eventual consistency)
## Opgave 2 
---
Design af et Distribueret System. 
I skal designe et simpelt distribueret system, der håndterer en webapplikation med følgende krav:
- Skal kunne håndtere brugere, der tilgår systemet via en webbrowser
- Skal bruge en Client-Server arkitektur
- Skal kunne distribuere forespørgsler til flere servere for at forbedre ydeevne
- Skal inkludere en kort beskrivelse af, hvordan systemet håndterer netværkskommunikation

![[DisrtibutedWebapplicationModelFromAssignment.png]]

🎤Præsentation Kl. 14:30 
- En tegning/model af systemet (”Håndtegnet”eller Digital)
- En kort beskrivelse af, hvordan systemet håndterer forespørgsler og svar

## Udvidet del
---
Udvid jeres system med følgende funktioner:
- Implementér fejltolerance, så systemet fortsætter med at fungere selv hvis en server går ned
- Beskriv hvordan I ville skalere systemet ved stigende brugerbelastning (horisontal vs. vertikal skalering)
- Overvej hvordan systemet kan bruge asynkron kommunikationtil at håndtere forespørgsler mere effektivt

🎤Præsentation Kl. 14:30
- En udvidet model med fejl-og skaleringshåndtering
- En kort beskrivelse af fordele og ulemper ved jeres løsning