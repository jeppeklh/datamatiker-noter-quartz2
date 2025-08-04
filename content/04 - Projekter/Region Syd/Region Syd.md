---
aliases:
  - Project 6
  - Projekt 6
---
#Projekt #RegionSyd 

[[Case Region Syddanmark.pdf|Case]]
[Artefakter](https://app.diagrams.net/#Wb!2ZvumUSy5kaTxX9DdntarkwBS9uu9EFMqt0PTZeH00WpAHjXfAitRIPCBFyVKFFi%2F01U5PXUQJ6O66XGMNIYVDLXONPY2IHHQG7#%7B%22pageId%22%3A%226lMOiL2-R7PofHDYw2A0%22%7D)
[Github Repo](https://github.com/Team-6-UCL-datamatiker/RegionSyd)
[Spørgsmålsark til RegionSyd](https://365ucl.sharepoint.com/:w:/r/sites/datamatiker-online-dmoof24-amg/_layouts/15/Doc.aspx?sourcedoc=%7BC99D3C7B-2186-449F-8C37-7852CB54292D%7D&file=Region%20Syd%20Sp%25u00f8rgsm%25u00e5l-Svar.docx&action=default&mobileredirect=true)

---

## Iteration 1

- [[Usecases (RegionSyd)]]
- Objektmodel
- Domænemodel
- SSD
- OC
- Wireframe

- [[SD (RegionSyd)#Iteration 1|SD]]
- DCD
- Databasemodel
- Kode

---

## Iteration 2
- Use Cases
- Objektmodel
- Domænemodel
- SSD
- OC
- Wireframe

- SD
- DCD
- Databasemodel
- Kode

---

## FAQ
![[Region Syd Case slide 1.png]]

Status (ambulance klar til tur osv. , hvilken slags type.)
5 forskellige installationer af 2 forskellige it-systemer. Der skal laves en fælles lokal database. 

Servicemål
En ambulance SKAL være fremme indenfor 15 min.
Har haft store problemer med at komme fra Vejle til Jelling på 15
Ny ambulancestation udenfor Vejle
Patientfragt - 3 timer
Hvad spares i tid og kroner
Som hovedregel liggende patienttransport
Én patient per bil. 
1 sikkerhedniveau (til autorisering)
Database kommer i første række. GUI er ikke så vigtigt, det er mest at kunne se at det virker.
Vi har som udgangspunnkt alt den information for patienter vi skal have (tænk ikke på GDPR)-

Spørgsmpl til borgere hvem skal have 1. prioeritet



Vi har bygget et system, der kan registrere og dele opgaver mellem regionerne. 
Det betyder, at disponenter fra f.eks. Region Syddanmark kan se, hvilke ambulancer der er tilgængelige, og hvilke opgaver der er planlagt i andre regioner. 

På den måde kan man koordinere og optimere brugen af ambulancerne for at undgå tomkørsler.

###### Opgaverne
Vi har en tabel, der indeholder informationer om hver opgave: beskrivelse af opgaven, hvornår den skal udføres, og status (er den ledig, tildelt eller afsluttet), servicemål
Giver et overblik over opgaver i systemet og disponent kan se hvordan opgaverkan kombineres


 ###### Lokationer
Vi registrerer start- og slutadressen for hver opgave. 
Dette gør det muligt at matche opgaver på en smart måde 
En ambulance, der er på vej tilbage fra København, kan få tildelt en ny opgave, hvor patienten skal transporteres til en destination på ruten.
  
###### Ambulancer
Vi holder styr på, hvor hver ambulance hører til, og hvilken status den har (ledig, på vej til opgave, optaget). 
Sp kan systemet foreslå, hvilke ambulancer der kan løse opgaver og undgå tomkørsler.

###### Disponenter
Vi registrerer, hvem der håndterer opgaverne. 
Det sikrer, at kun autoriserede brugere har adgang til systemet, og at de ved præcis, hvem der står for at disponere en opgave.