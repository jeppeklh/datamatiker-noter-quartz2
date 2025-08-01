
> [!tldr] Definition
Message Passing er en kommunikationsmetode, hvor **noder i et distribueret system sender og modtager beskeder** uden direkte afhængighed af hinanden. Beskeder kan være synkrone eller asynkrone og sendes via message brokers eller køsystemer.

## Struktur
---
- **Producent (Producer)**: Afsender en besked.
- **Broker (Message Queue/Event Bus)**: Mellemled, der distribuerer beskeder (f.eks. RabbitMQ, Kafka).
- **Forbruger (Consumer)**: Modtager og behandler beskeden.

## Fordele
---
**Løs kobling**: Afsenderen kender ikke nødvendigvis modtageren.  
**Skalerbart**: Flere forbrugere kan håndtere beskeder parallelt.  
**Fejltolerance**: Hvis en node fejler, kan beskeder gemmes og videresendes senere.  

## Ulemper
---
**Kompleks fejlhåndtering**: Beskeder kan gå tabt eller modtages flere gange.  
**Øget latenstid**: Asynkron kommunikation kan introducere forsinkelser.  

>[!example] Eksempler
>- **Apache Kafka**: Distribueret event-streaming platform.  
>- **RabbitMQ**: Message queue til kø-baseret kommunikation.  
>- **IoT-systemer**: Sensorer sender beskeder til en central hub.  

## Forbedringer
---
- **Retry & Dead Letter Queues**: Sikrer, at mistede beskeder kan behandles igen.  
- **Idempotens**: Gør services robuste over for duplikerede beskeder.  
- **Event Sourcing**: Gemmer beskedhistorik for genskabelse af systemets tilstand.  
