## Eksempel 
---
Du åbner en webside i browseren
Du skriver: `http://example.com`

### Det sker "bag kulissen" – lag for lag
---
**Lag 7 – Applikation**
Din browser laver en HTTP GET-anmodning.
Det ser fx sådan ud:
```vbnet
GET / HTTP/1.1
Host: example.com
```

**Lag 4 – Transport (TCP)**
HTTP-pakken pakkes ind i en TCP-segment.    
TCP sikrer, at data kommer frem i korrekt rækkefølge, og genudsender hvis pakker mangler.
  

**Lag 3 – Netværk (IP)**
TCP-segmentet pakkes ind i en IP-pakke.
IP sørger for, at pakken sendes til den rigtige server (f.eks. 93.184.216.34).    

**Lag 2 – Datalink (Ethernet/Wi-Fi)**
IP-pakken pakkes ind i en Ethernet-frame.
Den sendes via dit lokale netværk til routeren.

**Lag 1 – Fysisk**
Data sendes som elektriske signaler over kabel eller som radiobølger via Wi-Fi.    


## Eksempel: API-kald
---
### Lag 7 – Applikationslaget
---
**Formål** 
Giver brugerprogrammer adgang til netværkstjenester.

**Eksempel** 
En Blazor-klient kalder et REST API:

- `GET /api/user`

- HTTP-anmodning med cookie og evt. JSON i body (ved POST)

- HTTP-svar med JSON-data

- Blazor deserialiserer JSON til DTO og mapper til modelklasse    


### Lag 6 – Præsentationslaget
---
**Formål** 
Sikrer korrekt datapræsentation og sikkerhed.

**Eksempel:**
- Data krypteres (TLS ved HTTPS)

- Data dekrypteres på serveren

- JSON-formatering håndteres (serialisering/deserialisering)    


### Lag 5 – Sessionslaget
---
**Formål**
Opretter, vedligeholder og afslutter sessioner.

**Eksempel:**
- Klienten sender en cookie med en login-session

- Server validerer cookie og knytter anmodningen til en bruger

- Sessionen fastholdes på tværs af flere HTTP-kald


### Lag 4 – Transportlaget
---
**Formål**
Pålidelig transport af data mellem enheder.

**Eksempel**
- HTTP-anmodningen pakkes ind i et TCP-segment

- TCP sørger for fejlkontrol, pakkeordning og genforsendelse ved behov

- Forbindelse oprettes (TCP handshake: SYN, SYN-ACK, ACK)  


### Lag 3 – Netværkslaget
---
**Formål** 
Leverer pakker til den korrekte IP-adresse.

**Eksempel**
- TCP-segmentet pakkes ind i en IP-pakke

- IP-adressen (f.eks. 192.168.1.5 → 93.184.216.34) angiver destinationen

- Routere på vejen analyserer IP-headeren og videresender pakken    


### Lag 2 – Datalinklaget
---
**Formål** 
Sender data mellem to direkte forbundne enheder (f.eks. din PC til router).

**Eksempel**
- IP-pakken pakkes ind i en Ethernet-frame

- MAC-adresser bruges til at bestemme næste hop

- Ethernet, Wi-Fi eller andet protokolniveau bruges til transmission i lokalt netværk

### Lag 1 – Fysiske lag
---
**Formål** 
Overfører bits fysisk over et medie.

**Eksempel**
- Elektriske signaler (Ethernet-kabel), radiobølger (Wi-Fi) eller lysimpulser (fiber)

- 1-taller og 0’er sendes som analoge eller digitale signaler


## Eksempel: SignalR-chat 
---

### Lag 7 – Applikationslaget
---
**Hvad sker her:**
- En bruger skriver en chatbesked i en Blazor-komponent.

- SignalR-klienten kalder:  
    `await hubConnection.SendAsync("SendMessage", "Mads", "Hej")`

- På serveren fanger en `ChatHub` denne besked og sender den videre til alle tilsluttede klienter via `Clients.All.SendAsync(...)`.

**Protokol:** SignalR over WebSocket (eller fallback til HTTP/Long Polling)


### Lag 6 – Præsentationslaget
---
**Hvad sker her:**
- Beskeden (f.eks. JSON med brugernavn og besked) serialiseres.

- Hvis WebSocket er krypteret (wss://), bruges **TLS** til at kryptere data.

- Når serveren modtager det, dekrypteres det og deserialiseres igen.


**Eksempeldata:**
```json
["SendMessage", ["Mads", "Hej"]]
```


### Lag 5 – Sessionslaget
---
**Hvad sker her:**
- WebSocket-forbindelsen oprettes én gang og holdes åben.
    
- SignalR holder styr på, hvilken forbindelse der tilhører hvilken bruger.
    
- Der opretholdes en "session" via forbindelsen, typisk identificeret med connectionId.
    

**Her undgås klassiske cookies eller tokens i hvert kald**, da forbindelsen allerede er etableret.


### Lag 4 – Transportlaget
---
**Hvad sker her:**
- WebSocket-meldinger sendes som **rammer (frames)** over **TCP**.

- TCP sørger for:
    - At alle beskeder ankommer
    - At rækkefølgen er korrekt
    - Fejlhåndtering ved tabte pakker


### Lag 3 – Netværkslaget
---
**Hvad sker her:**
- TCP-segmenterne pakkes ind i IP-pakker.

- IP-adresser bruges til at sende data til den rigtige server og retur til klienten.



### Lag 2 – Datalinklaget
---
**Hvad sker her:**
- IP-pakker pakkes ind i Ethernet-frames (eller Wi-Fi), som sendes mellem fx din computer og routeren.

- MAC-adresser bruges til at levere data lokalt.


### Lag 1 – Fysiske lag
---
**Hvad sker her:**
- 1-taller og 0’er bliver til elektriske signaler (kabel) eller radiobølger (Wi-Fi).

- Data flyttes fysisk gennem netværket.


### Vigtig forskel ift. HTTP:
---
Ved HTTP/REST lukkes forbindelsen **efter hvert kald**.  
Ved WebSocket (SignalR) holdes forbindelsen **åben**, og både klient og server kan **sende data når som helst**.



