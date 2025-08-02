

>[!tldr] Definition
>Sikring af det producerede system bliver leveret til brugerne på en hensigtsmæssig måde. 
>
> Dette gøres ved hjælp af en **cutover-strategi**, som definerer, hvordan og hvornår overgangen fra et tidligere system (eller en tidligere version) til det nye system skal finde sted.

---

## Cutover-strategi

En cutover-strategi handler om at bestemme "hvornår man overgår" fra et tidligere system til det nye. Det dækker både scenarier, hvor et tidligere system var fysisk eller ikke-eksisterende, og scenarier, hvor man skifter fra en version til en anden. 
Dit valg af cutover-strategi skal baseres på:

- Den organisation, systemet skal udrulles i
- Den specifikke projektsituation
- Den valgte procesmodel

Nedenfor er nogle eksempler på cutover-strategier:

### Staged Deployment – Iscenesat udrulning

- **Beskrivelse:**  
  Opret et fuldt staging-miljø, hvor systemet udrulles og testes grundigt, indtil udrulningen forløber gnidningsfrit.
- **Anvendelse:**  
  Velegnet til systemer, hvor den primære udfordring ikke er selve brugen af systemet, men at gøre det tilgængeligt og operativt i driftsmiljøet. Denne strategi kan være nyttig, når systemkomponenter skal fungere som stand-alone applikationer, der kan arbejde offline og synkronisere data, når de kommer online.

### Gradual Cutover – Gradvis overgang

- **Beskrivelse:**  
  Overflyt brugerne gradvist til det nye system, så kun en mindre gruppe oplever de første fejl, mens superbrugere uddannes.  
- **Forudsætninger:**  
  Denne metode kan anvendes, hvis:
  - Det nye system er helt nyt og dækker funktioner, som ikke tidligere har været varetaget.
  - Det nye system er bagudkompatibelt med det gamle, og begge systemer kan dele data.
- **Eksempler:**  
  - Apps, hvor opdateringer udrulles gradvist.
  - Overgangsperioder, hvor nogle brugere stadig benytter det gamle system (fx Excel) mens andre skifter til det nye.

### Inkremental Cutover – Voksende udrulning

- **Beskrivelse:**  
  Udrul systemet i bidder, så organisationen kun skal forholde sig til en lille del af det nye system ad gangen.
- **Udfordringer:**  
  Kan være problematisk, hvis de forskellige dele af systemet er tæt integrerede eller afhængige af hinanden.
- **Anvendelse:**  
  Typisk anvendt i nyudviklede systemer, hvor det er hensigtsmæssigt at digitalisere enkelte forretningsprocesser gradvist. Det kan også være en god tilgang, hvis de tidligere systemer har været standalone-løsninger uden tæt integration.

### Parallel Testing

- **Beskrivelse:**  
  Kør både det nye og det gamle system sideløbende, og sammenlign output fra de to systemer.
- **Udfordringer:**  
  En dyr løsning, da to systemer skal driftes samtidig. Derudover lægger det et stort pres på brugerne, som skal udføre arbejdsprocesserne i begge systemer i overgangsperioden.
- **Anvendelse:**  
  Ofte benyttet i projekter, hvor det er meget vanskeligt at teste, og hvor fejl kan have store konsekvenser, fx i større lønsystemer med komplekse beregninger.

---

Ved at vælge den rette cutover-strategi kan udrulningen af systemet tilpasses både organisationens behov og de specifikke udfordringer, som projektet og procesmodellen medfører.

---

## Resourser
- [Fokusområde Læringsobjekt (Udulning)](https://rise.articulate.com/share/C9x7c641Qf8pDgT76Nqqy6ykP99dRgRJ#/lessons/R7q7YGmLJqco1SRCbLqWkUfEUPbnxC8u)