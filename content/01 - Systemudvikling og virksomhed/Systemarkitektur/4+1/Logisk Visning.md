
> [!tldr] Formål
>At understøtte de funktionelle krav ved at beskrive systemets struktur gennem objekter, klasser og relationer.
> [[4+1view-architecture.pdf#page=3&selection=0,1,2,24|4+1 p.3]]

Den måde, hvorpå systemets funktionelle krav deles op i moduler, klasser og relationer – især tydeligt i low-level design, hvor UML-diagrammer og objektorienterede principper (fx arv og komposition) kommer i spil.

---

## Kerneelementer
- **Objektorienteret decomposition:** Identificerer nøgleabstraktioner og klasser fra problemdomænet.
- **Diagrammer:** Anvender klassediagrammer, state charts og skabeloner til at visualisere strukturen og relationerne.
- **Genbrug og modularitet:** Fremmer genbrug af fælles mekanismer og services.

---

## Anvendelse
- Giver et klart billede af, hvad systemet skal levere, og hvordan de funktionelle elementer er organiseret.

> [!example] Eksempel
> Forestil dig et online butikssystem:
>- **Kunde:** En klasse der repræsenterer kunder med attributter som navn, e-mail og adresse.
>- **Produkt:** En klasse for varer med egenskaber som pris, lagerstatus og beskrivelse.
>- **Ordre:** En klasse der håndterer kundens ordrer, som forbinder Kunde og Produkt.
>- **Betaling:** En klasse der styrer betalingsprocessen og sikrer, at transaktionerne registreres korrekt.
>
> Et UML-klassediagram ([[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|Domænemodel]]) for dette system vil vise disse klasser og deres relationer – for eksempel at en Kunde kan afgive flere Ordrer, og at hver Ordre kan indeholde flere Produkter. Dette diagram giver et klart overblik over systemets struktur og de underliggende forretningsregler.
