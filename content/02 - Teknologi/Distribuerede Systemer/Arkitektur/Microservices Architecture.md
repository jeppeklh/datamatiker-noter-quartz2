>[!tldr] Definition 
>Microservices-arkitektur er en softwareudviklingsmetode, hvor en applikation opdeles i **små, uafhængige services**, der hver især håndterer en specifik funktion. Disse services kommunikerer via veldefinerede API’er og kan implementeres, deployes og skaleres individuelt.

![[MicroservicesArchitecture1.png]]

---

## Struktur
- **Service 1 (Brugerhåndtering)**: Håndterer autentifikation, brugerprofiler osv.
- **Service 2 (Ordrehåndtering)**: Styrer køb, betalinger og ordrer.
- **Service 3 (Lagerstyring)**: Holder styr på produkttilgængelighed.
- **Kommunikation**: Services taler sammen via **REST, gRPC eller event-messaging**.

---

## Fordele
**Skalerbarhed**: Hver service kan skaleres individuelt efter behov.  
**Fejltolerance**: Hvis én service fejler, påvirker det ikke nødvendigvis hele systemet.  
**Uafhængig udvikling**: Teams kan arbejde parallelt på forskellige services.  
**Bedre teknologifrihed**: Hver service kan skrives i forskellige programmeringssprog (polyglot architecture).  

---

## Ulemper
**Kompleksitet**: Kræver god orkestrering og overvågning.  
**Distribueret fejlhåndtering**: Fejl kan opstå på tværs af services.  
**Netværkslatens**: Flere API-kald kan øge responstid.  

---

## Kommunikation mellem Microservices
- **Synchronous (REST/gRPC)**: Direkte API-kald, hurtig respons, men afhængigheder kan skabe problemer.  
- **Asynchronous (Event-Driven Architecture - EDA)**: Services kommunikerer via events (Kafka, RabbitMQ), hvilket skaber løs kobling.  

>[!example] Eksempler
>- **Netflix**: Bruger microservices til streaming, brugerprofiler, anbefalinger osv.  
>- **Amazon**: Hver del af platformen (betaling, lager, anbefalinger) kører som en separat service.  
>- **Uber**: Har services til brugerbooking, kortdata, betaling, m.m.  

---

## Forbedringer
- **API Gateway**: Central indgang til systemet, der ruter trafik og sikrer autentifikation.  
- **Service Mesh (f.eks. Istio, Linkerd)**: Håndterer kommunikation, overvågning og sikkerhed mellem services.  
- **Containerization (Docker, Kubernetes)**: Gør det nemmere at deploye og skalere microservices.  

---

## Hvornår skal man bruge Microservices?
- Når systemet skal være **skalerbart og fleksibelt**.  
- Når **teams skal arbejde uafhængigt** på forskellige dele af applikationen.  
- Når der er **behov for høj fejltolerance**.  

 - **IKKE egnet** til små, simple applikationer – monolitter er ofte lettere at vedligeholde i sådanne tilfælde.  

![[UdvidetMicroService.png]]
![[UdvidetMicroServices2.png]]