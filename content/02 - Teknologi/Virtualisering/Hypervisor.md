> [!tldr] Definition
En software-, firmware- eller hardwarekomponent, der muliggør virtualisering ved at oprette og køre virtuelle maskiner. 
Den fungerer som et lag mellem den fysiske hardware og de virtuelle maskiner og styrer, hvordan ressourcerne fordeles.

Hypervisoren er central i virtualisering, da den sikrer effektiv fordeling af hardware-ressourcer og isolering mellem de virtuelle maskiner.
## Typer af Hypervisorer
---
##### Type 1 (Bare-metal)
  - Kører direkte på den fysiske hardware uden et underliggende operativsystem.
  - Anvendes ofte i enterprise- og datacentermiljøer.
  - Eksempler: VMware ESXi, Microsoft Hyper-V, Xen.
  
##### Type 2 (Hosted)
  - Kører oven på et host-operativsystem.
  - Velegnet til mindre miljøer, test og udvikling.
  - Eksempler: VMware Workstation, Oracle VirtualBox.
## Host og Guest
---
- **Host:** Den fysiske maskine, som kører hypervisor-softwaren. Hosten leverer den underliggende hardware, som hypervisoren benytter til at køre de virtuelle maskiner.
- **Guest:** De virtuelle maskiner, der kører oven på hosten. Hver guest maskine kører som en isoleret instans, og den eksisterer udelukkende i den virtuelle miljø, som hypervisoren skaber.

Denne inddeling muliggør effektiv udnyttelse af hardware-ressourcer og giver fleksibilitet i oprettelsen og styringen af virtuelle miljøer, hvilket er fundamentalt for virtualiseringsteknologier.

## Resourcer
---
- [Virtualisering LinkedIn Kursus (Hypervisor)](https://www.linkedin.com/learning/learning-virtualization-13945890/understanding-different-types-of-hypervisors?autoSkip=true&resume=false&u=57075649)