
> [!tldr] Formål
>At illustrere, hvordan softwarekomponenterne mappes til hardware, samt hvordan systemet deployeres på netværk og maskiner.
[[4+1view-architecture.pdf#page=8&selection=9,0,9,25|4+1 p.8]]

Overvejelser om, hvordan systemet skal deployeres – hardware, netværksinfrastruktur og eventuelle cloud-løsninger. Disse aspekter skal afstemmes med de overordnede designvalg og påvirker bl.a. hvordan grænseflader og integrationer udformes.
## Kerneelementer
---
- **Mapping:** Overfører elementer fra de logiske og processuelle visninger til fysiske noder.
- **Hardware og netværk:** Beskriver, hvordan processer distribueres på forskellige maskiner og via netværksinfrastruktur.
- **Skalérbarhed og ydeevne:** Fokus på performance, tilgængelighed og redundans gennem fysisk design.

## Anvendelse
---
- Anvendes til planlægning af deployment og sikring af, at systemet kan håndtere krav til ydeevne og pålidelighed.

> [!example] Eksempel
Forestil dig en distribueret webapplikation:
>- **Webservere:** Håndterer brugerforespørgsler og serverer webindhold.
>- **Applikationsservere:** Kører den centrale forretningslogik og behandler data.
>- **Databaseservere:** Opbevarer og administrerer systemets data.
>- **Load Balancer:** Fordeler trafik mellem serverne for at sikre høj tilgængelighed og belastningsbalancering.
>
Et fysisk arkitekturdiagram vil illustrere, hvordan disse komponenter er fordelt over flere maskiner eller datacentre og kommunikerer via netværk. Dette diagram hjælper med at sikre, at systemet kan skalere og forblive robust under forskellige belastningsforhold.

