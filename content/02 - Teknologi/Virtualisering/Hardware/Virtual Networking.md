> [!tldr] Definition
> Virtuelt netværk i en virtualiseret infrastruktur understøtter to primære scenarier:  
>1. Kommunikation mellem virtuelle maskiner (guests) på samme host.  
>2. Kommunikation mellem en virtuel maskine og eksterne systemer (internet, fysiske servere eller virtuelle maskiner på andre hosts).

---

## Kommunikation mellem virtuelle maskiner på samme host
- **Traditionel tilgang:**  
  Uden en dedikeret løsning kan en virtuel maskine (A) sende data til hostens fysiske netværksadapter. Dataene sendes derefter til en fysisk switch, som ruter trafikken tilbage til hosten, hvor den overleveres til den modtagende virtuelle maskine (B). Denne rute er funktionel, men ineffektiv, da trafikken unødvendigt forlader hosten.

- **Virtuel Switch:**  
  Mange hypervisor-leverandører tilbyder en virtuel switch, som opererer internt på hosten.  
  - **Fordele:**  
    - Direkte kommunikation mellem virtuelle maskiner uden at data forlader hosten.
    - Reduceret latency og bedre ydeevne.
  - **Funktion:**  
    - Når virtuel maskine A sender data til B, håndterer den virtuelle switch al trafik internt, hvilket eliminerer behovet for at gå via den fysiske netværksadapter.

---

## Kommunikation med eksterne systemer
- **IP- og MAC-adresser:**  
  - For at en virtuel maskine kan kommunikere med enheder uden for hosten, anbefales det, at hver virtuel maskine får tildelt sin egen IP- og MAC-adresse.  
  - I små miljøer kan VM'er sommetider dele hostens IP-adresse, men i større miljøer er det bedst at give hver VM unikke netværksidentiteter.

- **Dataudveksling:**  
  - Trafik fra virtuelle maskiner sendes via hostens fysiske netværksadapter og opfører sig identisk med trafik fra fysiske maskiner.  
  - For de fleste netværksenheder vil der ikke være nogen forskel på, om dataene kommer fra en fysisk eller en virtuel maskine.

---

## Resourcer
- [Virtualisering LinkedIn Kursus (Virtual Networking)](https://www.linkedin.com/learning/learning-virtualization-13945890/understanding-virtual-networking?resume=false&u=57075649)