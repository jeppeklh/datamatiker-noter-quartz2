
>[!tldr] Definition
> Distribution Transparency betyder, at **brugere og applikationer ikke behøver at kende til systemets underliggende distribuerede natur** – det fungerer, som om det var ét samlet system, selvom det består af mange noder.
> 
> [[Distributed_Systems_4.pdf#page=27&selection=15,0,15,25|p.11]]

---

## Typer af Distribution Transparency

| **Type**                                                                                          | **Beskrivelse**                                                                   |
| ------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| **Access Transparency**  [[Distributed_Systems_4.pdf#page=27&selection=45,0,46,0\|p.11]]<br>      | Brugere tilgår ressourcer på samme måde, uanset hvor de er placeret.              |
| **Location Transparency** [[Distributed_Systems_4.pdf#page=28&selection=49,0,50,0\|p.12]]<br>     | Ressourcers fysiske placering er skjult – de kan ligge hvor som helst i systemet. |
| **Replication Transparency** [[Distributed_Systems_4.pdf#page=29&selection=14,0,24,41\|p.13]]     | Brugere ser én ressource, selvom den er replikeret flere steder.                  |
| **Failure Transparency** [[Distributed_Systems_4.pdf#page=29&selection=44,0,58,44\|p.13]]         | Systemet skjuler hardware- eller softwarefejl og fortsætter uforstyrret.          |
| **Concurrency Transparency** [[Distributed_Systems_4.pdf#page=29&selection=28,0,43,12\|p.13]]     | Flere brugere kan tilgå en ressource samtidig uden konflikt.                      |
| **Migration Transparency** [[Distributed_Systems_4.pdf#page=28&selection=74,30,84,59\|p.12]]      | Ressourcer kan flyttes mellem noder uden at påvirke brugeren.                     |
| Relocation Transparency [[Distributed_Systems_4.pdf#page=28&selection=74,30,84,59\|p.12]]<br><br> |                                                                                   |
|                                                                                                   |                                                                                   |
---

## Fordele
**Forbedret brugervenlighed**: Ingen grund til at bekymre sig om, hvor ressourcer befinder sig.  
**Skalerbarhed**: Systemet kan vokse uden at ændre, hvordan ressourcer tilgås.  
**Øget robusthed**: Fejl og ændringer håndteres usynligt.  

---

## Udfordringer
**Øget kompleksitet**: At skjule detaljer kræver avanceret systemarkitektur.  
**Konsistensproblemer**: Hvis en ressource replikeres, skal den holdes opdateret alle steder.  
**Netværkslatens**: Transparens kan skjule forsinkelser i kommunikation mellem noder.  

---

## Løsninger & Strategier
- **Distributed File Systems** (f.eks. NFS, Google File System) sikrer **access & location transparency**. 
- **Load Balancers** og **proxies** skjuler den fysiske placering af tjenester.  
- **Consensus Protocols** (Raft, Paxos) hjælper med **replication transparency**.  
- **Self-healing Systems** (f.eks. Kubernetes) understøtter **failure transparency**.  

---

>[!example] Eksempler
>- **[[DNS]] (Domain Name System)**: Brugere indtaster en URL, men ved ikke, hvilken server der håndterer forespørgslen.  
>- **Cloud Storage (Google Drive, Dropbox)**: Brugere ser én mappe, men data kan ligge på mange servere.  
>- **Content Delivery Networks (CDN)**: Transparens i caching og load balancing gør, at brugere automatisk får data fra den nærmeste server.  
