---
aliases:
  - Middleware
---
>[!tldr] Definition
Middleware er et softwarelag, der fungerer som en **bro mellem applikationer og de underliggende systemer** i et distribueret miljø. Det skjuler kompleksiteten af netværkskommunikation og giver tjenester såsom sikkerhed, load balancing og datahåndtering.
> [[Distributed_Systems_4.pdf#page=89&selection=32,0,32,10|p.73]]


## Funktioner
---
- **Kommunikation**: Understøtter meddelelsesorienteret kommunikation (f.eks. RabbitMQ, Kafka).  
- **Datahåndtering**: Abstraherer adgangen til databaser og filsystemer.  
- **Sikkerhed**: Håndterer autentifikation, autorisation og kryptering.  
- **Fejlhåndtering**: Hjælper med at gøre systemet robust over for fejl.  
- **Load Balancing**: Fordeler forespørgsler mellem flere servere for optimal ydeevne.  

## Typer af Middleware
---

| **Type**             | **Beskrivelse** |
|----------------------|----------------|
| **Message-Oriented Middleware (MOM)** | Bruges til kø-baseret kommunikation (f.eks. Apache Kafka, RabbitMQ). |
| **Remote Procedure Call (RPC) Middleware** | Gør det muligt for applikationer at kalde funktioner på eksterne noder (f.eks. gRPC, Thrift). |
| **Database Middleware** | Muliggør adgang til distribuerede databaser (f.eks. JDBC, ODBC). |
| **Transaction Middleware** | Håndterer distribuerede transaktioner (f.eks. X/Open XA). |

## Wrappers & Interceptors
---
Middleware bruger ofte **wrappers** og **interceptors** til at modificere og håndtere kommunikation eller funktionalitet på en fleksibel måde. 
### Wrappers 

>[!tldr] Definition
En **wrapper** (også kaldet en "proxy" eller "adapter") er et softwarelag, der **indpakker en eksisterende komponent eller funktion** for at ændre dens adfærd eller skjule kompleksitet. 

>[!example] Eksempel 
>- En **database-wrapper** kan gøre det muligt for en applikation at interagere med flere forskellige databaser uden at ændre sin kode. 
>- I **RPC-middleware** kan en wrapper oversætte funktionskald mellem forskellige programmeringssprog. 
### Interceptors 

>[!tldr] Definition
En **interceptor** er en mekanisme, hvor middleware kan **aflytte, modificere eller blokere** en anmodning, før den når sin destination. 

>[!example] Eksempel
>- En **sikkerhedsinterceptor** kan kontrollere, om en bruger har de rette adgangsrettigheder, før en API-forespørgsel behandles. 
>- En **logningsinterceptor** kan registrere alle kald til en microservice uden at ændre selve microservice-koden.

| **Feature** | **Wrapper**                                  | **Interceptor**                                          |     |
| ----------- | -------------------------------------------- | -------------------------------------------------------- | --- |
| Formål      | Indpakker og ændrer en komponent             | Aflytter og manipulerer anmodninger                      |     |
| Placering   | Rundt om en ressource (f.eks. database, API) | Indsættes i et kalds-flow (f.eks. HTTP request pipeline) |     |
| Eksempler   | JDBC-driver, API-proxies                     | Authentication middleware, Logging middleware            |     |

## Fordele
---
**Abstraherer kompleksitet**: Udviklere behøver ikke håndtere lav-niveau netværksprotokoller.  
**Forbedrer interoperabilitet**: Understøtter forskellige platforme og programmeringssprog.  
**Øger systemets pålidelighed**: Indbygget fejlhåndtering og load balancing.  

## Udfordringer
---
**Kan introducere latenstid**: Yderligere softwarelag kan øge responstiden.  
**Konfigurationskompleksitet**: Middleware kan kræve avanceret opsætning og tuning.  
**Sikkerhedsrisici**: Skal sikres mod angreb som Man-in-the-Middle (MitM).  

>[!example] Eksempler
>- **Apache Kafka** – Message-Oriented Middleware til event-streaming.  
>- **gRPC** – RPC-middleware, der muliggør højtydende service-til-service kommunikation.  
>- **Kubernetes Service Mesh (f.eks. Istio, Linkerd)** – Middleware til orkestrering af microservices.  

