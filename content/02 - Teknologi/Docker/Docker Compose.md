> [!tldr] Definition
> Gør det muligt at definere og køre multi-container applikationer ved hjælp af en enkelt YAML-fil. Det er ideelt til komplekse setups, hvor flere services (f.eks. webserver, database, cache) skal samarbejde.

---

## Nøglefunktioner
- **Enkelt konfigurerbare miljøer**  
  Hele miljøet defineres i en `compose.yaml`-fil med services, netværk, volumes og porte.  
   Én fil = nem opsætning og dokumentation.  

- **Automatiseret afhængighedshåndtering**  
  Brug `depends_on` for at sikre korrekt start-rækkefølge.  
  Netværk oprettes automatisk, så containere kan tale sammen.  

- **Konsistens på tværs af miljøer**  
  Samme Compose-fil kan bruges i udvikling, test og produktion.  
   Færre “works on my machine”-problemer.  
  Miljøvariabler understøttes for fleksibel konfiguration.  

- **Effektivt udviklingsworkflow**  
  Start alt med `docker compose up`.  
  Luk ned med `docker compose down`.  
  Ingen grund til manuelle netværk/volumes/flags.  
  Skalering er nemt med `--scale`.

---

## Compose vs. Dockerfile
- **Dockerfile**: Instruktioner til at *bygge* et image.  
- **Compose-fil**: Beskriver *hvordan* containere kører og interagerer.

---

## Eksempel på brug
1. **Klon en sample app**  

```bash
git clone https://github.com/dockersamples/todo-list-app
cd todo-list-app
```

2. **Start appen med Compose**

```bash
docker compose up -d --build
```
Dette vil:
- Hente images (Node.js, MySQL)
- Oprette netværk og volumes
- Starte containere med korrekt config

3. **Stop og fjern alt**
```bash
docker compose down
```
Tilføj `--volumes` for også at fjerne persistente data.

---

## GUI-support
Docker Desktop gør det muligt at styre Compose stacks visuelt.  
Se, start/stop, og slet containere og netværk med få klik.

---

## Resourcer
- [Docker Compose Dokumentation](https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-docker-compose/)
