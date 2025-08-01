> [!tldr] Definition
  En enkelt integreret applikation, hvor alle funktioner – brugergrænseflade, forretningslogik, dataadgang – er samlet i én kodebase.
  >
  Hvis al applikationskode er samlet i én kodebase og kører som én enhed (selvom den kommunikerer med en ekstern database), betragtes det stadig som en **monolitisk arkitektur**
  [[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=160&selection=32,0,32,10|p.124]]

Et system er monolitisk, hvis:
1. **Forretningslogikken** er samlet i én kodebase.
2. Applikationen **kører som én enhed** (selvom den bruger en ekstern database).
3. Deployment sker som én samlet applikation.
4. Systemet **kan ikke opdeles i selvstændige dele**, der kan køre uafhængigt.
## Fordele
---
  - Simpel implementering for små applikationer.
  - Ingen kompleks netværkskommunikation mellem dele.
  
## Ulemper
---
  - Tæt kobling mellem funktionerne gør ændringer vanskelige.
  - Skal forstå hele systemets opbygning fra starten, hvilket kan gøre vedligeholdelse og skalering udfordrende.
  - Agility er næsten umuligt

Hele programmet er en stor executable unit. 
Tæt kobling - små ændringer i systemet kan skabe problemer andre steder
## Resourcer
---
- [Systemarkitektur Monolith LinkedIn ](https://www.linkedin.com/learning/software-architecture-foundations/monoliths?resume=false&u=57075649)