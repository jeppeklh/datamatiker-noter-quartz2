

> [!tldr] Formål
>At adressere ikke-funktionelle krav som ydeevne, samtidighed og pålidelighed ved at beskrive systemets dynamiske adfærd.
[[4+1view-architecture.pdf#page=4&selection=81,0,81,24|4+1 p.4]]

Beslutninger om, hvordan systemets komponenter kører, kommunikerer og håndterer samtidighed. I high-level design træffes ofte valg, der påvirker performance og skalerbarhed (fx klient/server, komponentbaseret arkitektur).
## Kerneelementer
---
- **Samtidighed:** Opdeling af systemet i processer og tråde, der kører parallelt.
- **Kommunikationsmekanismer:** Beskriver inter-proces kommunikation via beskeder, RPC, event-broadcasting osv.
- **Ydeevne:** Fokus på optimering af responstid og belastningsfordeling ved at allokere funktioner til passende processer.

## Anvendelse
---
- Bruges til at designe, analysere og optimere den dynamiske opførsel af systemet.

> [!example] Eksempel
Forestil dig et banktransaktionssystem:
>- **Transaktionsproces:** En proces, der håndterer og validerer finansielle transaktioner.
>- **Loggerproces:** En separat proces der registrerer transaktioner og hændelser for revision.
>- **Meddelelsesproces:** Håndterer asynkrone beskeder mellem de forskellige processer, f.eks. for at bekræfte, at en transaktion er gennemført.
>
Et diagram over disse processer vil vise, hvordan de kører parallelt og kommunikerer via beskeder eller andre synkroniseringsmekanismer. Dette sikrer, at systemets dynamiske adfærd opfylder kravene til både sikkerhed, performance og pålidelighed.
