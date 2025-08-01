
> [!tldr] Definition
En **Docker Registry** er et centralt lager, hvor container‐images kan opbevares, versioneres og deles mellem udviklings‑ og produktionsmiljøer.
Github for Docker
## Nøglefunktioner
---
- **Central opbevaring & distribution**  
  Gem og hent images fra ét fælles sted, så alle teams og systemer bruger præcis samme version.  
- **Versionsstyring & tagging**  
  Organisér images med tags (f.eks. `latest`, `stable`, `v1.2.3`) for enkel rollback og historik.  
- **Sikkerhed & adgangskontrol**  
  Konfigurer tilladelser, scan for sårbarheder, signér images og krypter overførsler.  
- **CI/CD‑integration**  
  Webhooks og automatiske builds/pushes sikrer, at nye images testes og deployes uden manuel indgriben.  

## Typer af registries
---
- **Offentlige registries**  
  - Docker Hub (default) med over 100.000 offentlige images.  
  - Indeholder både Official Images, Verified Publishers og Docker‑Sponsored Open Source.  
- **Privat registry**  
  - Hostet selv (f.eks. Harbor, JFrog Artifactory).  
  - Cloud‑tilbud som Amazon ECR, Azure Container Registry (ACR) eller Google Container Registry (GCR).  

## Registry vs. Repository
---
- **Registry:** Det overordnede system, der gemmer og håndterer alle dine container‐images.  
- **Repository:** En konkret “mappe” i registry’en, der indeholder relaterede images (typisk samme applikation med forskellige tags).

## Eksempler på anvendelse
---
1. **Team‑samarbejde**  
   Del et image med kolleger via et privat repository, så alle arbejder med identiske miljøer.  
2. **CI/CD pipelines**  
   Push automatisk nybyggede images til registry, trig deployment‑jobs og testmiljøer.  
3. **Kompani‑infrastruktur**  
   Kør eget registry for at beskytte forretningskritiske images bag firmastyring og compliance.

## Resourcer
---
- [Docker Registry Dokumentation](https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-registry/)