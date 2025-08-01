> [!tldr] Definition
En privat [[Cloud Computing|cloud]] er en cloud-løsning, hvor organisationen virtualiserer størstedelen af sin infrastruktur – ofte 90-100% af serverne – til at køre forretningskritiske applikationer. Når man designer en privat cloud, er der flere nøgleområder, der skal tages i betragtning:

## Centrale Overvejelser
---
### Storage
- **Kompatibilitet:**  
  Forskellige hypervisorer understøtter forskellige filsystemer. Det er vigtigt at sikre, at lagringsløsningen er kompatibel med den valgte hypervisor.
- **Kvantitet og kvalitet:**  
  Estimér, hvor meget lagerplads der kræves, og vælg højtydende storage, da lagringssystemet ofte kan blive en flaskehals.

### Bandwidth
- **Lokal båndbredde:**  
  Hver virtuel maskine genererer trafik, så netværket skal kunne håndtere den samlede belastning, særligt ved brug af netværksbaseret storage.
- **Fjernbåndbredde:**  
  Ved live migration mellem hosts på forskellige lokationer kræves der tilstrækkelig båndbredde til hurtig dataoverførsel. Overvej opgraderinger, hvis den nuværende kapacitet ikke er tilstrækkelig.

### Uptime og Driftssikkerhed
- **Uptime mål:**  
  Definér et realistisk uptime-mål (f.eks. 99.9% eller højere), da 100% uptime ikke er praktisk muligt.
- **Redundans og live migration:**  
  Ved at distribuere de virtuelle maskiner over flere hosts kan man udføre vedligeholdelse eller reagere på problemer ved at flytte VM’er uden nedetid. Overvej også at placere hosts på forskellige lokationer for at beskytte mod lokale afbrydelser.

### Skalerbarhed
- **Fremtidige behov:**  
  Lav et overslag over, hvor mange virtuelle maskiner og hosts der er nødvendige i dag, og hvordan behovet kan udvikle sig over de næste år.
- **Fleksibilitet:**  
  En privat cloud skal kunne tilpasses ændringer i arbejdsbyrden og teknologiske fremskridt uden store omkostninger.

## Leverandørløsninger og Værktøjer
---
### Microsoft
- **Hyper-V:**  
  Microsofts hypervisor, der muliggør servervirtualisering.
- **System Center Virtual Machine Manager:**  
  Et værktøj til administration af store virtuelle miljøer med funktioner som live migration og automatiseret administration.

### VMware
- **vSphere ESXi:**  
  En type 1 hypervisor, der kører direkte på hardwaren.
- **vMotion:**  
  Håndterer live migration mellem hosts.
- **DRS (Distributed Resource Scheduler):**  
  Automatisk belastningsbalancering ved at flytte virtuelle maskiner fra overbelastede til underudnyttede hosts.
- **vCloud Director (del af vCloud Suite):**  
  Værktøjer til hurtig provisioning og administration af en privat cloud.

## Resourcer
---
- [Virtualisering LinkedIn Kursrs (Design af private cloud)](https://www.linkedin.com/learning/learning-virtualization-13945890/designing-a-private-cloud?resume=false&u=57075649#)