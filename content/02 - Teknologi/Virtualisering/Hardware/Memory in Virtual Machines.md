
> [!tldr] Definition
I virtualiserede miljøer håndterer hypervisoren tildelingen af fysisk hukommelse til gæstemaskiner. Det er vigtigt at skelne mellem begrebet *virtual memory* i en traditionel computer og den måde, hukommelse administreres i virtuelle maskiner.

## Hukommelsesallokering i Virtuelle Maskiner
---
- **Fysisk Hukommelse:**  
  Hypervisoren tildeler et segment af den fysiske hukommelse til hver gæstemaskine, som gæsten kan læse og skrive til uden begrænsninger fra den øvrige drift.

- **Fast og Dynamisk Hukommelse:**  
  Mange hypervisorer giver mulighed for at sætte en fast mængde hukommelse til en gæstemaskine, eller definere et interval (minimum og maksimum). Dette gør det muligt for hypervisoren at tildele ekstra hukommelse, når en gæst begynder at løbe tør, og samtidig frigøre hukommelse, når hosten er presset.

## Memory Reclamation og Ballooning
---
- **Memory Reclamation:**  
  Når en host bliver lav på hukommelse, vil hypervisoren forsøge at genvinde hukommelse fra gæstemaskiner. Dette kan dog udgøre en risiko, hvis der utilsigtet fjernes hukommelse, der indeholder vigtige data.

- **Ballooning:**  
  For at imødekomme dette benytter moderne hypervisorer en teknik kaldet *ballooning*.  
  - En lille komponent, en såkaldt *balloon driver*, indsættes i gæstemaskinen, som kan "blæses op" og optage ekstra hukommelse, der ikke indeholder kritisk data.
  - Denne hukommelse kan derefter sikkert genindvindes af hypervisoren.  
  - Det er dog bedst at undgå for meget ballooning, da det medfører en vis overhead og potentielt kan nedsætte ydeevnen. En optimal løsning er at tilføje mere fysisk hukommelse til hosten.



## Resourcer
---
- [Virtualisering LinkedIn Kursus (Memory in Virtual MAchines)](https://www.linkedin.com/learning/learning-virtualization-13945890/understanding-virtual-memory?resume=false&u=57075649)