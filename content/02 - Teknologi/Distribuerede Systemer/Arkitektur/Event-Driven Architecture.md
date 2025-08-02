---
aliases:
  - EDA
---

>[!tldr] Definition
> Event-Driven Architecture er en softwarearkitektur, hvor systemet reagerer på **events** (begivenheder), i stedet for at følge en sekventiel proces. Events kan være brugerhandlinger, systemhændelser eller beskeder mellem services.
>
> [[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=166&selection=46,0,47,7|p.130]]

---

## Struktur
- **Producent (Producer)**: En komponent, der genererer events (f.eks. en bruger klikker på en knap).  
- **Broker (Event Bus/Message Queue)**: En middleware, der distribuerer events (f.eks. Kafka, RabbitMQ).  
- **Forbruger (Consumer)**: En komponent, der reagerer på events og udfører handlinger.  

---

## Fordele
**Løs kobling**: Komponenter interagerer via events uden direkte afhængigheder.  
**Skalérbarhed**: Systemet kan håndtere mange events parallelt.  
**Reaktivt**: Hurtig respons på hændelser uden blokering.  

---

## Ulemper
**Debugging kan være svært**: Svært at spore, hvor et event blev genereret.  
**Kompleksitet**: Kræver god arkitektur for at undgå race conditions og data-inkonsistens.  
**Fejlhåndtering**: Hvis et event mistes, kan systemets tilstand blive inkonsistent.  

>[!example] Eksempler
>- **Apache Kafka**: En distribueret event-streaming platform.  
>- **Microservices**: Bruger ofte events til at kommunikere mellem services.  
>- **IoT-systemer**: Sensorer sender events, som behandles af forskellige systemer.  

---

## Forbedringer
- **Event Sourcing**: Gemmer events som en log for nem fejlfinding og genskabelse af systemets tilstand.  
- **CQRS (Command Query Responsibility Segregation)**: Adskiller læse- og skriveoperationer for at forbedre ydeevne.  
- **Retry & Dead Letter Queues**: Sikrer, at events ikke går tabt, hvis en service fejler.  
