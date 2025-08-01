> [!tldr] Definition
Udvider [[Client-Server Model|client/server-modellen]] ved at introducere et eller flere mellemliggende lag (tiers) mellem klient og server.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=161&selection=19,0,25,23|p.125]]
## Varianter
---
  - **To-tier:** Klient og server er adskilt. [[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=162&selection=18,0,19,17|p.126]]
  - **Three-tier:** Inkluderer et mellemlag (middle tier) for at isolere klient og server. [[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=162&selection=24,1,28,18|p.126]]

## Fordele
---
  - Øget fleksibilhed og uafhængighed mellem lag.
  - Ændringer i et lag kræver som regel mindre tilpasning i de andre lag.

> [!note] Note
Multitier er i øvrigt bedst practice pga. seperationen. Det er sjældent at applikationer bruger mere en 3 lag. 
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=163&selection=70,0,72,12|p.127]]