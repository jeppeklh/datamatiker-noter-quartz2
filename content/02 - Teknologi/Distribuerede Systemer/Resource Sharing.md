
>[!tldr] Definition
> Resource Sharing betyder, at flere computere (noder) i et distribueret system **deler ressourcer** såsom processorkraft, lagerplads, netværk og data for at forbedre effektiviteten og samarbejdet.
> [[Distributed_Systems_4.pdf#page=26&selection=33,0,33,16|p.10]]

---

## Typer af delte ressourcer
- **Hardware**: CPU, RAM, netværksbåndbredde, printere.
- **Data**: Filer, databaser, caches.
- **Software**: Applikationer, webservices, API'er.
- **Processer**: Tjenester, der kører i baggrunden og leverer funktionalitet til flere brugere.

---

## Fordele
**Øget effektivitet**: Optimerer brugen af systemressourcer.  
**Reduceret omkostning**: Deling af ressourcer eliminerer behovet for redundante systemer.  
**Skalerbarhed**: Flere noder kan dele belastningen.  
**Forbedret samarbejde**: Lettere adgang til fælles data og tjenester.  

---

## Udfordringer
**Konkurrence om ressourcer**: Flere noder kan kræve adgang til samme ressource samtidig.  
**Sikkerhed**: Skal forhindre uautoriseret adgang til delte ressourcer.  
**Fejltolerance**: Systemet skal håndtere fejl i en delt ressource uden at påvirke hele netværket.  

---

## Løsninger & Strategier
- **Load Balancing**: Fordeler arbejdsbyrden jævnt mellem noder.  
- **Caching**: Reducerer behovet for gentagne anmodninger om de samme ressourcer.  
- **Replica Management**: Opretholder kopier af data for at undgå flaskehalse.  
- **Access Control & Security Policies**: Regulerer, hvem der kan tilgå hvilke ressourcer.  

>[!example] Eksempler
>- **Cloud Computing**: AWS, Google Cloud og Azure tilbyder delte computerressourcer.  
>- **Distribuerede databaser**: NoSQL-databaser som Apache Cassandra understøtter datadeling mellem mange noder.  
>- **Fildelingstjenester**: Dropbox og Google Drive bruger distribueret lagring.  
