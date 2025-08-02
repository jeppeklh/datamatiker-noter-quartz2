---
aliases:
  - Distributed Systems
---
>[!tldr] Definition
> Et **distribueret system** er en samling af uafhængige computere, der samarbejder som én enhed for at opnå et fælles mål. De kommunikerer via netværk og deler ressourcer.

---

## Karakteristika
- **Decentralisering**: Ingen enkelt enhed har fuld kontrol.
- **Fejltolerance**: Systemet skal kunne håndtere fejl i enkelte noder.
- **Konsistens vs. Tilgængelighed**: Ofte en afvejning mellem disse to (se CAP-teoremet).
- **Skalérbarhed**: Systemet kan håndtere øget belastning ved at tilføje flere noder.
- **Concurrency**: Flere noder arbejder parallelt.
- [[Resource Sharing]]
- [[Distribution Transparency]]

---

## Udfordringer
- **Netværksfejl**: Latens, pakketab, og partitionering kan forekomme.
- **Replikering**: Hvordan sikrer man data er konsistente på tværs af flere noder?
- **Koordination**: Distribuerede systemer kræver ofte en form for synkronisering.
- **Fejlhåndtering**: Systemet skal håndtere delvise nedbrud uden at stoppe helt.

---

## CAP-teoremet
CAP-teoremet siger, at et distribueret system kun kan opnå to ud af tre egenskaber:
1. **Konsistens (C)** – Alle noder ser de samme data på samme tid.
2. **Tilgængelighed (A)** – Systemet svarer altid på forespørgsler.
3. **Partitionstolerance (P)** – Systemet fungerer trods  netværksforbindelsen mellem noder er afbrudt.

---

## Populære Modeller
- [[Client-Server Model|Client-Server]]: En central server håndterer anmodninger fra klienter.
- [[Peer-to-Peer Model| Peer-to-Peer]] (P2P): Ingen central server, alle noder kommunikerer direkte.
- [[Microservices Architecture]]: Applikation opdeles i små, uafhængige services, der hver især håndterer en specifik funktion.
- [[Event-Driven Architecture|Event-Driven Architecture]]: Systemet reagerer på events i stedet for direkte forespørgsler.

---

## Konsistensmodeller
- **Strikt Konsistens**: Alle noder ser opdateringer øjeblikkeligt.
- **Eventual Konsistens**: Data bliver ens over tid, men kan være forskellige midlertidigt.
- **Causal Konsistens**: Opdateringer der er kausalt forbundne, respekteres.

---

## Kommunikation
- **Synchronous vs. Asynchronous**: Skal man vente på svar, eller kan man fortsætte?
- **Message Passing**: Kommunikation sker via beskeder (f.eks. gRPC, RabbitMQ).
- **Remote Procedure Call (RPC)**: Kald af funktioner på eksterne noder.

---

## Fejltolerance & Konsensus
- **Leader Election**: Hvordan vælges en leder i et system? (Raft, Paxos)
- **Two-Phase Commit (2PC)**: Bruges i distribuerede databaser for at sikre transaktionsintegritet.
- **Byzantine Fault Tolerance (BFT)**: Beskytter mod onde noder.

---

## Eksempler på Distribuerede Systemer
- **Google Spanner** – Distribueret database med stærk konsistens.
- **Apache Kafka** – Event-streaming platform.
- **Amazon DynamoDB** – Eventual consistent NoSQL database.

---

## Vigtige Koncepter
- **Microservices**: Software opdelt i små, uafhængige services.
- **Load Balancing**: Fordeling af trafik mellem flere servere.
- **Sharding**: Opdeling af data på tværs af noder for bedre skalering.
- **Quorum**: Beslutninger kræver flertal af noder.
- [[Middleware (Distributed Systems)|Middleware]]: Softwarelag, der håndterer kommunikation, sikkerhed og dataudveksling mellem applikationer.

---

## Resourser
- [Distributed Systems Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_34/scormcontent/index.html#/lessons/gM1LAWplUvaQrLXF_8aGaICVz44hh6J_)
