---
aliases:
  - Images
---
> [!tldr] Definition
> Et **Docker Image** er en standardiseret, read-only pakke bestående af alle filer, binære programmer, biblioteker og konfigurationsfiler, der er nødvendige for at køre en container.

---

## Nøgleprincipper
- **Uforanderlighed (Immutable):** Når et image er bygget, kan det ikke ændres. Ændringer skaber et nyt image.  
- **Lag (Layers):** Images består af flere lag. Hvert lag repræsenterer ændringer i filsystemet (tilføj, fjern, modificer filer). Lagene caches for hurtigere genbygning.

---

## Anvendelse og eksempler
1. **Base images**  
   - Eksempel: `python:3.10`, `node:18`  
   - Bruges som fundament for at bygge din applikation – indeholder kun runtime og nødvendige systempakker.

2. **Service images**  
   - Eksempel: `postgres:15`, `redis:7`  
   - Kører standardtjenester med forudkonfigurerede indstillinger, så du hurtigt kan starte databaser, caches mv.

3. **Custom images**  
   - Start fra et base image og tilføj dine afhængigheder og kode via en `Dockerfile`.  
   - Eksempel:
     ```dockerfile
     FROM python:3.10-slim
     WORKDIR /app
     COPY requirements.txt .
     RUN pip install -r requirements.txt
     COPY . .
     CMD ["python", "app.py"]
     ```

---

## Distribution og registries
- **Docker Hub:** Standardregistry med over 100.000 offentlige images.  
- **Docker Trusted Content:**
  - **Official Images:** Kuraterede, sikre images fra Docker.
  - **Verified Publishers:** Kommercielt vedligeholdte, verificerede images.
  - **Docker‑Sponsored Open Source:** Open source‑projekter sponsoreret af Docker.

> [!tip] Tip
>  Integrer registry-push/pull i dine CI/CD‑pipelines for automatisk build, test og deployment, og brug tags (f.eks. `latest`, `v1.2.3`) til versionsstyring.

---

## Resourcer
- [Docker Images Dokumentation](https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-an-image/)
- [Docker Images best practices](https://docs.docker.com/build/building/best-practices/)