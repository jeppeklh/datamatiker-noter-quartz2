---
aliases:
  - RPC
---

>[!tldr] Definition
> Remote Procedure Calls (RPC) er en kommunikationsmodel, hvor **en applikation kalder en funktion på en ekstern server, som om det var en lokal funktion**. RPC kan være **synkron** (blokkerende) eller **asynkron**.

---

## Struktur
- **Klient**: Kalder en ekstern funktion.  
- **Server**: Udfører den ønskede handling og returnerer et svar.  
- **Stub (Proxy)**: Skjuler netværkskommunikation og gør fjernkald gennemsigtige.  

---

## Fordele
**Gennemsigtighed**: Klienten behøver ikke kende detaljer om serverens implementering.  
**Hurtigere end HTTP-baserede API’er**: Letvægtsprotokoller som gRPC har lav overhead.  
**Understøtter flere programmeringssprog**: Mange RPC-rammer genererer kode til forskellige sprog.  

---

## Ulemper
**Stramt koblede systemer**: RPC kræver kendskab til serverens API.  
**Fejl kan være svære at håndtere**: Netværksfejl kan stoppe kaldet helt.  
**Ofte synkront**: Klienten skal vente på svar, hvilket kan påvirke ydeevnen.  

>[!example] Eksempler
>- **gRPC**: Google’s højtydende RPC-framework, baseret på Protocol Buffers.  
>- **Thrift**: Apache’s RPC-protokol, der understøtter flere sprog.  
>- **JSON-RPC**: Simpelt RPC-format, der bruger JSON over HTTP.  

---

## Forbedringer
- **Load Balancing**: Brug af proxies til at fordele kald mellem flere servere.  
- **Asynkron RPC**: Tillader klienter at fortsætte med andre opgaver, mens de venter på svar.  
- **Timeouts & Retries**: Sikrer, at systemet ikke hænger ved netværksfejl.  
