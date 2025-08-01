> [!tldr] Definition
En **container** er en isoleret, letvægts‑proces, der pakker din applikation sammen med alle dens nødvendige afhængigheder og kører på værtens kerne, men i sit eget filsystem og netværksrum.

## Hvorfor bruge containere?
---
- **Isolation:** Én applikations miljø forstyrrer ikke andre applikationer eller dit host‑system.  
- **Portabilitet:** Samme container kører ens fra din udviklingsmaskine til CI/CD‑miljøet og videre til produktion.  
- **Effektivitet:** Flere containere deler samme kerne – langt mindre overhead end virtuelle maskiner.  
- **Konsistens:** Du undgår “det virker på min maskine”‑problemer, da alt nødvendigt er bundlet.

## Kort definition
---

>[!tldr] Definition
>Container = Isoleret proces + dens afhængigheder pakket i et filsystem (read‑only layers + ét skrivebar layer).

## Eksempler på anvendelse
---
1. **Web‑arkitektur med mikroservices**  
   - Kør frontend, backend og database i hver sin container for nem udvikling og skalering.  
2. **Testmiljøer**  
   - Spinn hurtigt en PostgreSQL, Redis eller anden service op lokalt uden at installere på værts‑OS.  
3. **CI/CD pipelines**  
   - Byg og test applikationen i en container, så testmiljøet altid er identisk med produktion.  
4. **Eksperimenter med nye teknologier**  
   - Prøv en ny database eller et nyt programmeringssprog uden at rode med din lokale installation.

## Resourcer
---
- [Docker Containers Dokumentation](https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/)
- 