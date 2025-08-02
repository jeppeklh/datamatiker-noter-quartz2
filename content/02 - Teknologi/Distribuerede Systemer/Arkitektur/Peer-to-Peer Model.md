---
aliases:
  - P2P
---

>[!tldr] Definition
> I et **P2P-system** er der ingen central server. Alle noder (peers) fungerer både som **klienter** og **servere**, hvilket betyder, at de kan anmode om og levere data til hinanden direkte.

![[Peer2PeerArchitecture.png]]

---

## Struktur
- **Decentraliseret**: Ingen central kontrol eller server.
- **Hver node er både klient og server**: Peers deler ressourcer mellem sig.
- **Netværkskommunikation**: Kan være struktureret (DHT) eller ustruktureret.

---

## Fordele
**Ingen central flaskehals**: Systemet bliver ikke afhængigt af én server.  
**Høj skalerbarhed**: Flere noder betyder højere kapacitet.  
**Robusthed**: Hvis en peer går offline, kan systemet stadig fungere.  

---

## Ulemper
**Inkonsekvent ydeevne**: Nogle peers kan være langsomme eller upålidelige.  
**Data-konsistens kan være svær at opretholde**.  
**Sikkerhed**: Sværere at kontrollere, da der ikke er en central autoritet.  

>[!eexample] Eksempler
>- **BitTorrent**: Filoverførsler mellem brugere uden en central server.  
>- **Blockchain (Bitcoin, Ethereum)**: Distribueret hovedbog, hvor alle noder validerer transaktioner.  
>- **Skype (tidligere P2P-model)**: Opkald blev videresendt mellem brugere uden en central server.  

---

## Forbedringer
- **Distributed Hash Table (DHT)**: En struktureret måde at finde peers på i netværket.  
- **Kryptering**: For at forbedre sikkerheden og beskytte data.  
- **Hybrid P2P**: En kombination af P2P og Client-Server, f.eks. hvor en server bruges til at koordinere peers.  
