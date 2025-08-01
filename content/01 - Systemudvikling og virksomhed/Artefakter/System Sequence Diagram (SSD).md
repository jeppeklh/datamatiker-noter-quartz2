tags: #Systemudvikling #Artifact
## Definition
---
[[applying-uml-and-patterns-3rd.pdf#page=272&selection=0,12,0,36|Larman kapitel 10]]

En System Sequence Diagram (SSD) er et UML-diagram, der visualiserer interaktionen mellem eksterne aktører og et system, der behandles som en "black box". 
SSD'er fokuserer primært på de systemhændelser, som aktørerne genererer, samt deres rækkefølge.

Formålet med SSD'er er at tydeliggøre, hvilke hændelser der kommer ind i systemet, da dette er et vigtigt skridt i at designe software, der kan håndtere disse hændelser.
([[applying-uml-and-patterns-3rd.pdf#page=277&selection=2,0,17,55|Larman p.277]])

SSD'er giver et overblik over systemets adfærd uden at specificere, hvordan det internt fungerer.
([[applying-uml-and-patterns-3rd.pdf#page=277&selection=18,0,33,7|Larman p.277]])

Informationen i SSD'er er ofte kortfattet. Yderligere detaljer om operationer, parametre og data kan beskrives i en [[Glossary]], der fungerer som en slags ordbog for systemet.
([[applying-uml-and-patterns-3rd.pdf#page=282&selection=0,52,18,60|Larman p.282]])

Lav ikke et SSD for alle scenarier
([[applying-uml-and-patterns-3rd.pdf#page=284&selection=2,0,7,50|Larman p.284]])


#### SSD Bruges til: 
---
- Identificere systemhændelser genereret af eksterne aktører.

- Fastlægge rækkefølgen af hændelser i et specifikt scenarie.

- Forstå systemets grænseflade og interaktioner.

- Dokumentere arkitekturen, især når man skal forstå eksisterende systemer.


## Relation til Use Cases
---
En SSD viser systemhændelser for et specifikt scenarie i en use case. SSD'en genereres derfor ved at inspicere en use case.
([[applying-uml-and-patterns-3rd.pdf#page=279&selection=0,51,18,1|Larman p.279]])

Stort set en 1 til 1 kopi af en [[Use Case]]
Beskriver aldrig mere end 1 [[Use Case]]!


## Relation til UP
---
SSDs er en del af Use-Case Modellen i [[Unified Process|UP]]. 
([[applying-uml-and-patterns-3rd.pdf#page=284&selection=9,0,16,47|Larman p.284]])
De er især nyttige i [[Unified Process#UP faser|elaboration]] fasen, hvor man identificerer detaljer om systemhændelser for at:

- Klargøre hvilke operationer systemet skal håndtere.

- Udarbejde system operationskontrakter.

- Understøtte estimering af projektets omfang.
## Kvalitetskriterier
---
#### Er
- Kunne se sammenhæng med [[Use Case]]
- Kunne se sammenhæng mellem data'en der sendes ind i systemet og attributer i [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|domænemodellen]]
#### Er ikke!
- Sikre at operationernes navne svarer til et forretningsmæssigt formål
- Sikre at SSD'en understøtter en god brugeroplevelse
- Sikre at antallet af operationer stemmer overens med wireframen

#### Viser
---
- Aktørens interaktion med systemet

#### Viser ikke
- Kundens interaktion med brugergrænsefladen
- Brugerens interaktion med softwaren
- Data flowet gennem alle dele af systemet




Ud fra dette SSD skal der laves 3 [[Operatrion Contracts (OC)|operation contracts]]
![[SSD.png]]