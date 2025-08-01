> [!tldr] Definition
TCP står for **Transmission Control Protocol**, og det er en af de vigtigste protokoller i internettets kommunikation. Den arbejder på **transportlaget** i [[OSI-modellen|OSI]]-modellen (lag 4).
>
Forestil dig TCP som et **anbefalet brev med kvittering**. Du sender en pakke, og du får besked, når modtageren har fået den – og hvis den ikke kommer frem, bliver den sendt igen.

---


### Eksempel
---
Når du går ind på en hjemmeside via din browser:

Din browser opretter en TCP-forbindelse til webserveren (via port 80 for HTTP eller 443 for HTTPS).

Den sender en HTTP-anmodning gennem TCP.

Serveren svarer via TCP med websiden.

Alt dette sker på få millisekunder – og TCP sørger for, at intet går tabt.