---
aliases:
  - VDI
---
> [!tldr] Definition
> Adresserer mange af de udfordringer, organisationer oplever med at vedligeholde fysiske desktops. Med fysiske desktops kan hver enhed have forskellig hardware, operativsystem og software, hvilket komplicerer fejlfinding og opgraderinger. VDI centraliserer administrationen ved at levere en standardiseret virtuel desktop til alle brugere.

---

## Hvordan virker VDI?
- **Centraliseret administration:**  
  En central server hoster en master-VM, som bliver kopieret og tildelt til brugerne, når de logger på.  
- **Dumb terminal-koncept:**  
  Lokale enheder fungerer primært som terminaler (med tastatur, mus og skærm), mens den egentlige behandling foregår på serveren.
- **Brugeroplevelse:**  
  Da den virtuelle maskine leveres dynamisk, ses de fleste processer som om de kører lokalt, selvom alt behandles eksternt.

---

## Fordele ved Desktop-Virtualisering
- **Forenklet fejlfinding:**  
  Ved at køre en standardiseret VM for alle brugere reduceres variationen, og support kan fokusere på én konfiguration.
- **Effektive opgraderinger:**  
  Opgraderinger og softwareændringer udføres centralt på master-VM'en, hvilket eliminerer behovet for manuel opdatering af hver enkelt fysisk maskine.
- **Lavere hardwareomkostninger:**  
  Lokale enheder kan være simple og billige, da den meste behandling foregår på serveren.
- **Skalerbarhed:**  
  Nye brugere kan hurtigt tilføjes ved blot at forbinde en simpel terminal til netværket og tildele dem en kopi af den virtuelle desktop.

---

## Vigtige overvejelser
- **Datahåndtering:**  
  Da den virtuelle desktop typisk ikke gemmer en lokal kopi ved logout, skal brugerne gemme dokumenter på netværksdrev for at undgå datatab.
- **Forskellige brugerbehov:**  
  Selvom en ensartet VM ofte er ideel, kan forskellige afdelinger kræve specielle konfigurationer, hvilket kan medføre, at der skal oprettes flere forskellige VM-billeder.
- **Leverandørløsninger:**  
  Markedets førende VDI-løsninger omfatter Citrix XenServer, VMware Horizon og Microsofts VDI-funktionalitet (bygget ovenpå Hyper-V).

---

## Resourcer
- [Virtualisering LinkedIn Kursus (VDI)](https://www.linkedin.com/learning/learning-virtualization-13945890/virtualizing-desktop-computers?resume=false&u=57075649)
- 