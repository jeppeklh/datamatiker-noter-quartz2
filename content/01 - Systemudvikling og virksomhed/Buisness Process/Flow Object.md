Beskriver hvad der sker I processen

## Events
---
Repræsenterer en hændelse I forretningsprocessen
En hændelse er noget der sker
Eks. Man modtager en besked, der går 5 minutter, der opstår en fejl, et tilbud bliver afslået osv.
Events deles op I 3 typer:
#### Start event
---
Et event der starter hele processen. Der er kun ét startevent I hele processen
![[Start Event.png]]
#### Intermediate event
---
Events der sker undervejs I processen.
Kan være noget der stopper eller pauser processen, eller afventes for at fortsætte processen
![[Intermediate Event.png]]
#### End event
---
Et event der afslutter hele processen
Alle grene af processen skal ende I samme event
![[End Event.png]]


## Activities
---
Reprænterer en aktivitet I forretningsprocessen
En aktivitet er en handling, der udføres som en del af processen

#### Task symbol
---
En task er den mest basale form for aktivitet
![[Task.png]]
#### Transaction symbol
---
En specialiseret sub-process, der indeholder en betaling
![[Transaction.png]]

#### Sub-process symbol
---
En gruppe af tasks, der hænger naturligt sammen
#### Call symbol
---
En global sub-process.
Global betyder at sub-processen genbruges flere steder I det samlede buisness flow
![[Call.png]]

## Gateways
---
Et gatewaysymbol repræsenterer en forgrening eller et valg i den forretningsproces, der beskrives i modellen
#### Basal gateway
---
Den basale gateway er typisk brugt i "hvis-så-ellers" beslutninger.
Det er væsentligt, at alle udfald er dækket, da man ellers risikerer, at processen stoppes uden det var hensigten
![[Gateway.png]]