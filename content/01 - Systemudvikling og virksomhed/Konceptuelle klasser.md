tags: #Systemudvikling

## Definition 
---
En konceptuel klasse er en abstrakt repræsentation af en "ting" eller "entitet" i den virkelige verden, som systemet skal kunne håndtere eller modellere.

Det er ikke en specifik kodeklasse (altså ikke noget, der direkte eksisterer i programkoden endnu), men en konceptuel eller teoretisk model af de ting, som systemet beskæftiger sig med.



De hjælper med at identificere de vigtigste elementer og relationer i et system.

Ved at definere konceptuelle klasser kan du tydeliggøre, hvordan forskellige dele af systemet hænger sammen og interagerer.

De er grundlaget for den videre designproces, hvor disse klasser omdannes til kodeklasser i det egentlige program.

##### Eksempel
Hvis du udvikler en app til en bibliotek, kunne konceptuelle klasser være _Bog_, _Bruger_, og _Lån_.
## Identificering
---
Du skal gennemgå kravspecifikationen og se efter substantiver (navneord), som kan repræsentere de centrale koncepter i systemet.

Nogle af de ting, du skal lede efter, er aktører, ting, steder, og begivenheder.

##### Eksempel
I en kravspecifikation til et bibliotekssystem kan ord som "bog", "bruger" og "låneperiode" identificeres som mulige konceptuelle klasser.
## Egenskaber
---
Hver konceptuel klasse har typisk nogle _egenskaber_ (attributter), som beskriver klasseinstanserne, og _ansvar_, som beskriver de ting, klassen skal kunne.

Egenskaber kan være f.eks. bogens titel, forfatter, udgivelsesår osv., mens ansvar kan være at finde ud af, om en bog er tilgængelig eller ej.

##### Eksempel
- Klasse: _Bog_
- Egenskaber: _titel_, _forfatter_, _udgivelsesår_
- Ansvar: _erTilgængelig()_

## Relationer
---
Relationer viser, hvordan konceptuelle klasser hænger sammen og interagerer med hinanden.

Relationerne kan f.eks. vise, hvordan en _Bruger_ kan låne en _Bog_ gennem et _Lån_-objekt.

##### Eksempel
En _Bruger_ kan have en relation til _Lån_, og et _Lån_ har en relation til _Bog_.

På diagrammet vises disse relationer ofte som pile eller linjer mellem klasserne, hvilket kan hjælpe med at forstå deres indbyrdes forbindelser.


## Fra koncept til Designklasse
---
Når de konceptuelle klasser er identificeret og visualiseret i et klassediagram, kan du bruge dem som grundlag for at designe de faktiske klasser i koden.

Konceptuelle klasser bliver til _designklasser_, hvor du går mere i dybden med, hvordan de skal implementeres i kode, hvilke metoder de skal have, og hvordan de præcist interagerer i programmet.

## Resources
---
- [Konceptuel Klasse Læringsobjekt](https://rise.articulate.com/share/ys3rdLiYnQCTz4SC6PxuubJZIcaUM_FC#/lessons/8vk70F1mNC7QCzH0OLN8ICScAAyrHvI2)
- 