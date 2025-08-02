> [!tldr] Definition
> Client-server modellen er en arkitektur, hvor en **central server** håndterer anmodninger fra én eller flere **klienter**. Serveren er ansvarlig for at levere ressourcer, data eller tjenester til klienterne.

![[ClientServerArchitecture.png]]

---

## Struktur
**Klienter** 
Enheder, der anmoder om data eller tjenester (f.eks. webbrowser, mobilapp).

**Server**
En central enhed, der behandler anmodninger og returnerer svar.

**Netværk** 
Klienter og server kommunikerer via et netværk (f.eks. internet, LAN).

---

## Fordele
**Centraliseret kontrol** 
Serveren administrerer ressourcer, sikkerhed og data.  

**Enkel at vedligeholde** 
Opdateringer sker centralt på serveren.  

**Forudsigelig ydeevne** 
Klienter interagerer kun med én server, hvilket gør latency og responstid mere forudsigelig.  

---

## Ulemper
**Single Point of Failure (SPOF)** 
Hvis serveren fejler, er hele systemet nede.  

**Skaleringsudfordringer** 
Høj belastning på serveren kan kræve load balancing.  

**Netværksafhængighed** 
Hvis forbindelsen fejler, kan klienten ikke få adgang til data.  


> [!example] Eksempler
>- **Webapplikationer**: En browser (klient) anmoder om data fra en webserver. ([[Distributed_Systems_4.pdf#page=101&selection=54,0,54,16|p.85]]) 
>- **Databaser**: Klienter sender SQL-forespørgsler til en central database-server.  
>- **Online spil**: Spilklienter opretter forbindelse til en central server for matchmaking og spilstatus.  

---

## Forbedringer
- **Load balancing**: Fordeling af trafik mellem flere servere.  
- **Caching**: Gemme ofte brugte data for at reducere belastningen på serveren.  
- **Replikering**: Flere servere synkroniseres for at øge tilgængelighed og skalerbarhed.  

Sættes op vertikalt
> ([[Distributed_Systems_4.pdf#page=105&selection=26,0,26,74|p.89]])

UI, processing components, Datamanagement
> ([[Distributed_Systems_4.pdf#page=104&selection=50,0,51,74|p.88]])

---

## Database Replication
https://www.geeksforgeeks.org/types-of-database-replication-system-design/

https://www.geeksforgeeks.org/comparison-centralized-decentralized-and-distributed-systems/