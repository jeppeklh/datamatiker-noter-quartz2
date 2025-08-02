
>[!tldr] Definition
> RESTful API’er og gRPC er populære metoder til **service-til-service kommunikation** i distribuerede systemer. REST bruger **HTTP og JSON**, mens gRPC er en **binær [[Remote Procedure Calls|RPC]]-protokol** udviklet af Google.

---

## RESTful API’er
- Baseret på HTTP-verber (**GET, POST, PUT, DELETE**).  
- Brugervenligt og let at debugge.  
- Tekstbaseret kommunikation (JSON, XML), hvilket kan være langsomt.  
Se [[REST]]

---

## gRPC
- Baseret på **Protocol Buffers (Protobuf)**, som er hurtigere og mere kompakt end JSON.  
- Understøtter **streaming** og **bi-direktionel kommunikation**.  
- Kræver mere opsætning end REST, men giver bedre ydeevne.  

---

## Fordele
**REST**: Simpelt og let at forstå, bredt understøttet.  
**gRPC**: Høj ydeevne, understøtter flere sprog, binær dataoverførsel.  
**Begge**: Skalerbare og velegnede til microservices.  

---

## Ulemper
**REST**: Mere overhead, da JSON er tungere end Protobuf.  
**gRPC**: Mere kompleks opsætning og kræver Protobuf-kompilering.  

---

## Hvornår bruger man hvad?
- **REST**: Når man har brug for bred kompatibilitet og enkelhed.  
- **gRPC**: Når høj ydeevne og lav latency er vigtig, f.eks. i microservices.  

>[!example] Eksempler
>- **REST**: Typisk brugt i **webservices** og **API'er til frontend**.  
>- **gRPC**: Bruges af **Google Cloud, Kubernetes, og Netflix** til hurtig service-til-service kommunikation.  

---

## Forbedringer
- **GraphQL**: Alternativ til REST, hvor klienter kan forespørge præcis de data, de har brug for.  
- **Caching**: Reducerer netværkstrafik ved at gemme ofte brugte svar.  
- **API Gateway**: Central indgang til at håndtere REST/gRPC-kald sikkert og effektivt.  

---

## Resourcer
- [Distributed Systems Læringsobjekt (Kommunikation)](https://scorm.itslearning.com/data/3289/C20150/ims_import_34/scormcontent/index.html#/lessons/ga2GZl-OT4uDGb9M2mOlJdiTyS_ML08M)