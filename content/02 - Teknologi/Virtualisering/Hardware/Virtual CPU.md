---
aliases:
  - vCPU
---
> [!tldr] Definition
Den virtuelle repræsentation af en fysisk processor (pCPU). Med moderniseringen af hypervisor-teknologier er der sket en betydelig udvikling i, hvordan CPU-ressourcer allokeres til virtuelle maskiner.

## Ældre vs. Moderne Metoder
---
- **Ældre metode:**  
  Tidligere blev virtualisering håndteret ved, at hypervisoren direkte tildelte en fysisk CPU til en virtuel maskine, hvilket skabte et 1:1-forhold mellem pCPU og vCPU.

- **Moderne metode – Time Division:**  
  I stedet for et fast forhold deles den fysiske CPU's tid i cyklusser, som tildeles en fælles pulje af vCPU'er. Dette muliggør **oversubscription**, hvor flere vCPU'er allokeres end der fysisk er CPU-ressourcer.

## Oversubscription
---
> [!tldr] Definition
  Oversubscription betyder, at der tildeles flere virtuelle processorer, end hvad de fysiske CPU'er kan levere i realtid.

- **Effekter:**  
  Når ressourcerne er knappe, kan nogle vCPU'er opleve kortvarige forsinkelser (f.eks. pauser på et par millisekunder), hvilket potentielt kan påvirke ydeevnen.

- **Prioritering:**  
  Avancerede hypervisorer understøtter ofte prioritering af vCPU'er, så kritiske virtuelle maskiner får fortrinsret til CPU-cyklusser, mens mindre vigtige maskiner kan "springe over" et par cyklusser.

## Anbefaling
---
For optimal ydeevne anbefales det, at oversubscription kun anvendes som en kortsigtet løsning. Ideelt set bør forholdet mellem vCPU'er og pCPU'er være tæt på 1:1, hvilket ofte opnås ved at opgradere den fysiske hardware.


## Resourcer
---
- [Virtualisering LinkedIn Kursus (vCPU)](https://www.linkedin.com/learning/learning-virtualization-13945890/understanding-virtual-cpu?resume=false&u=57075649)