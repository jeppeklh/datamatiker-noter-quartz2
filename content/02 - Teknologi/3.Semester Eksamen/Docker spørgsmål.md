### Hvorfor har I valgt at bruge Docker – og kun til SQL Server?
Vi bruger Docker til SQL Server for at gøre opsætningen mere ensartet på tværs af udviklingsmiljøer. 
Det betyder, at vi ikke behøver installere SQL Server lokalt, og alle får den samme version og konfiguration. 

Vi har ikke dockeriseret hele appen endnu, fordi det er lettere at udvikle Blazor/.NET i Visual Studio med debugging, hot reload osv. 
Docker bruges her primært som et udviklingsværktøj til databasen.

---

### Hvilke fordele og ulemper er der ved jeres nuværende opsætning?
**Fordele:**
- Nem og hurtig opsætning af SQL Server.
- Ens databaseversion for hele teamet.
- Adskillelse af databasen fra udviklingsmiljøet.
    

**Ulemper:**
- Applikationen er ikke containeriseret, hvilket kan give uoverensstemmelser mellem udviklings- og produktionsmiljø.
- Ingen automatiseret opstartsrækkefølge eller afhængighedskontrol mellem app og database (endnu).
- Der mangler en løsning til seed/migrations i nuværende setup.

---

### Hvordan ville I udvide setup’et, hvis appen også skulle dockeriseres?
Vi ville oprette en Dockerfile til Blazor/.NET-applikationen og tilføje en ekstra service i `docker-compose.yml`, fx:

```yaml
webapp:
  build: .
  ports:
    - "5000:80"
  depends_on:
    - sqlserver
```

Vi ville sikre netværksadgang til databasen via servicens navn (`sqlserver`), og muligvis bruge environment-variabler til connection string. 
Derudover kunne vi bruge volumes til persistens og Docker Secrets til credentials.

---

### Hvordan sikrer I, at databasen er klar, inden appen starter?
Det kan gøres med `depends_on` kombineret med et `healthcheck`. `depends_on` sikrer opstartsrækkefølge, men **ikke** at databasen er klar – derfor bruges `healthcheck` til at sikre, at SQL Server faktisk er klar til at modtage forbindelser:

```yaml
depends_on:
  sqlserver:
    condition: service_healthy
```

---

### Hvordan fungerer netværket mellem jeres app og databasen i Docker?
Docker Compose opretter automatisk et internt netværk, hvor hver service kan tilgås via sit servicenavn. 
Appen kan derfor connecte til databasen via `Server=sqlserver;` i connection string. Det fungerer som DNS internt i Docker-netværket.

---

### Hvad skal man overveje, hvis databasen flyttes til produktion med Docker?
**Persistens** 
Volumes skal bruges, så data ikke slettes ved genstart.

**Sikkerhed** 
Brug stærkere passwords og helst secrets til credentials.

**Backup-strategi** 
Automatiserede backups og restore-muligheder skal være på plads.

**Netværk og adgang** 
Begræns ekstern adgang, fx kun via applikationen.

**Performance** 
Sørg for, at ressourcer (CPU/RAM/diske) er konfigureret til produktionsbehov.

**Monitoring** 
Implementér overvågning og logging af containeren.

---

### Hvordan ville I håndtere migrations eller seed-data i denne opsætning?
Vi kunne bruge `dotnet ef database update` som en del af appens startup (enten manuelt eller automatisk i containerens entrypoint). 
Alternativt kunne vi have et separat “init” script eller en container, som håndterer seed og migrations.

Eksempel:

```dockerfile
ENTRYPOINT ["dotnet", "ef", "database", "update", "&&", "dotnet", "MyApp.dll"]
```

---

### Hvorfor har vi kun en docker-compose-fil – og ikke en Dockerfile?
Fordi **vi ikke bygger vores egen image** – vi bruger et færdiglavet image (SQL Server), som vi bare konfigurerer og starter med `docker-compose`.

Med andre ord:

- **docker-compose.yml** bruges her til at køre en _færdig_ container (SQL Server).

- **Dockerfile** er **ikke nødvendig**, fordi vi **ikke har brug for at bygge noget selv** endnu.


Hvis vi skulle dockerisere jeres Blazor/.NET app, så ville vi tilføje en **Dockerfile til den app**. 
Så ville `docker-compose` både styre SQL Server og jeres egen container med appen – og så havde vi brug for **begge filer**.


|Filtype|Bruges til|Bruges hvornår?|
|---|---|---|
|`Dockerfile`|Bygge en container til din app|Når du laver din egen app-container|
|`docker-compose.yml`|Starte/orkestrere containere|Når du vil køre flere services sammen (fx db + app)|

---

### Hvordan ville CI/CD-processen se ud, hvis I dockeriserede hele appen?
En typisk CI/CD-pipeline kunne se sådan ud:

**CI (bygning):**

- Checkout kode.
	
- Kør tests.
	
- Byg Docker-billeder (app + evt. database seed tool).
	
- Push images til et container registry.
	
**CD (deployment):**

- Pull images.
	
- Kør `docker-compose up` på produktionsserver eller via Kubernetes.
	
- Kør migrations som del af deployment.
	
- Monitorer healthchecks og logs.
	

Vi kunne bruge GitHub Actions, Azure DevOps, eller GitLab CI til at automatisere dette flow.

---

##  Et typisk flow – step for step
### Udvikling lokalt
---
Du skriver kode og en `Dockerfile`.
  
Du bygger et image med:
```bash
 docker build -t mitteam/appnavn .
```

Du tester det lokalt med:
```bash
docker run -p 5000:80 mitteam/appnavn
```
    
---

### CI/CD – Build og push image
Når du laver en push/merge til `main`, starter CI/CD-pipelinen. Den gør:

**Build image**:
```bash
docker build -t mitteam/appnavn:latest .
```

**Login til registry**:
```bash
echo $REGISTRY_PASSWORD | docker login ghcr.io -u $USER --password-stdin
```

**Push image til registry**:
```bash
docker push ghcr.io/mitteam/appnavn:latest
```


Eksempel på registry:
- `ghcr.io` (GitHub Container Registry)
- `docker.io` (Docker Hub)
- `myregistry.azurecr.io` (Azure)
    
---

### Deployment til cloud (eks. Azure)
Når image er pushet, trækker cloud-platformen det:

Azure Web App (Container Instance) eller Kubernetes laver:
```bash
docker pull ghcr.io/mitteam/appnavn:latest
```

Appen startes som container:
```bash
docker run -d -p 80:80 ghcr.io/mitteam/appnavn:latest
```

---

### Hvordan hjælper det teamet?
- **Alle har samme miljø** – ingen "det virker kun på min maskine".
    
- **Ingen lokal database nødvendig** – alt er i containere.
    
- **CI/CD sikrer**, at alle pushes giver ny version i skyen.
    
- **Rollbacks** er lette – man kan starte en tidligere image-version igen.
    
---

### Ekstra: Hvis du vil gøre det endnu bedre
- Brug **tags** som `:latest`, `:v1.0.1`, `:commitSHA` for versionsstyring.
    
- Tilføj **container scanning** (sikkerhed) i pipelinen.
    
- Brug **Docker Compose** hvis I har flere services (frontend, backend, db).
    
- Tilføj **staging miljø**, så man tester før man deployer til prod.
  
  Mere et distribureret system. Vi har en fælles sqlserver i en container.
   