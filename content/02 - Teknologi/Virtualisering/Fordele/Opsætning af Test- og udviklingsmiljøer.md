> [!tldr] Definition
> Virtualisering muliggør oprettelsen af fleksible testmiljøer, som kan anvendes både permanent og midlertidigt. Ved at virtualisere testmiljøer kan organisationer hurtigt rulle ændringer ud, udføre belastningstests og let gendanne en tidligere, stabil tilstand ved fejl.

---

## Permanent Testmiljø
- **Formål:**  
  Anvendes f.eks. af et eCommerce-websted til at teste ændringer, før de rulles ud i produktionen.
- **Fordele:**
  - **Snapshots/Checkpoints:**  
    Gør det muligt at tage et "øjebliksbillede" af en virtuel maskines tilstand, så man hurtigt kan rulle tilbage, hvis der opstår problemer.
  - **Skalerbarhed:**  
    Det er nemt at ændre ressourcerne (f.eks. antal processorer) for at teste, hvordan systemet håndterer forskellige belastninger.
  - **Kloning af produktionsmiljøet:**  
    Ved at klone produktionsservere kan testmiljøet spejle den nøjagtige konfiguration, hvilket reducerer fejlkilder.

- **Sikkerhed:**  
  Vær opmærksom på at undgå kopiering af følsomme data under kloning, så testmiljøet ikke utilsigtet indeholder data, der bør beskyttes.

---

## Midlertidigt Testmiljø
- **Scenarie:**  
  F.eks. evaluering af en ny regnskabsløsning over en periode på 90 dage.
- **Fordele:**
  - **Omkostningseffektivt:**  
    Ingen behov for at investere i nyt hardware til et kortvarigt projekt.
  - **Fleksibilitet:**  
    En ny virtuel maskine kan hurtigt oprettes og installeres med den ønskede software.
  - **Cloud-baserede løsninger:**  
    Hvis der ikke er et eksisterende virtualiseret miljø, kan man leje en server fra en public cloud-udbyder (f.eks. Amazon AWS, Microsoft Azure eller via spot instances med timepriser) til den ønskede testperiode.

---

## Resourcer
- [Virtualisering LinkedIn Kursus (Test- og UdviklingsMiljø)](https://www.linkedin.com/learning/learning-virtualization-13945890/setting-up-test-and-development-environments?resume=false&u=57075649)
