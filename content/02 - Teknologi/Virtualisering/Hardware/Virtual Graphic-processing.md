---
aliases:
  - vGPU
---
> [!tldr] Definition
> Grafikbehandling i virtuelle maskiner er et område, der endnu ikke er helt modent, primært fordi mange gæstemaskiner – som oftest er servere (f.eks. e-mail, web eller filservere) – ikke har et stort behov for avanceret grafik. Derfor fokuserer mange hypervisor-leverandører ikke på at tildele dedikerede grafikressourcer.

---

## Nøglepunkter
- **Direkte GPU-adgang:**  
  Nogle hypervisorer giver mulighed for, at en gæstemaskine kan få direkte adgang til den fysiske GPU i hosten. Dog er det typisk sådan, at en host kun har én GPU, hvilket begrænser adgangen til en enkelt gæst ad gangen.

- **Emergerende vGPU-teknologi:**  
  En lovende udvikling er specialiserede chips, der muliggør deling af en fysisk GPUs grafikbehandlingskraft mellem flere virtuelle maskiner. Denne teknologi kaldes en **vGPU (virtual GPU)** og fungerer på en måde, der minder om fordelingen af virtuelle CPU'er, hvor flere vGPU'er trækker fra et fælles pulje af grafikressourcer efter behov.

- **Modenhed og anvendelse:**  
  Selvom avanceret grafik ikke er et krav for mange serverbaserede applikationer, bliver delte grafikløsninger (vGPU) stadig vigtigere for dem applikationer, der kræver grafikacceleration i et virtualiseret miljø.

---

## Resourcer
- [Virualisering LinkedIn Kursus (Graphic-processing)](https://www.linkedin.com/learning/learning-virtualization-13945890/understanding-virtual-graphic-processing?resume=false&u=57075649)