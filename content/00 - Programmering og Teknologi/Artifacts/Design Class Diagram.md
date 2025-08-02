
[[applying-uml-and-patterns-3rd.pdf#page=382&selection=0,18,0,38|Larman kapitel 16.2]]

Et UML-diagram (Unified Modeling Language), der visuelt repræsenterer klasser, interfaces og deres indbyrdes forhold. 
Det bruges til statisk objektmodellering, hvilket betyder at det beskriver den strukturelle opbygning af et system, men ikke den dynamiske adfærd.

Bruges til at modellere softwareklasser og deres relationer. 
Dette kaldes ofte for et Design Class Diagram (DCD), og det er en del af Design Modellen i UP.
([[applying-uml-and-patterns-3rd.pdf#page=382&selection=2,90,13,7|Larman p.382]])

Statisk ([[applying-uml-and-patterns-3rd.pdf#page=341&selection=0,0,20,25|Larman p.341]])

---

## Anvendelse
Class diagrammer har en bred vifte af anvendelser i objektorienteret analyse og design:

**Visualisering af domænemodellen:** 
 De kan bruges til at illustrere de konceptuelle klasser i domænet, deres attributter og associationer.

**Design af softwareklasser:** 
De kan bruges til at definere klasser, interfaces, attributter, metoder og relationer mellem softwareklasser.

**Dokumentation af systemstrukturen:** 
Class diagrammer fungerer som en visuel dokumentation af systemstrukturen, der kan deles med interessenter og udviklere.

**Kommunikation**: 
De kan bruges som et redskab til at kommunikere designidéer og løsninger mellem udviklere og interessenter.

---

## Retningslinjer
##### Inkludér associationer og attributter
Identificér associationer mellem klasser og specificér vigtige attributter. Klasser og deres associationer skal afspejle de konceptuelle klasser fra domænemodellen.
##### Tænk som en korttegner
Brug nøjagtige og konsistente domænespecifikke navne til klasser og attributter, så diagrammet kan forstås af forretningsfolk.
##### Brug sammensætning frem for aggregering
Når én klasse klart ejer en anden klasse, skal du bruge sammensætning i stedet for aggregering for at vise ejerskab
##### Undgå overdrevet brug af arv
Brug arv med omtanke. Arv kan skabe problemer med fleksibilitet og vedligeholdelse, hvis det anvendes forkert
##### Modellér attributter som typer, ikke klasser
Gør det kun til en klasse, hvis det er et koncept med adfærd og identitet i domænet.

---

## Kvalitetskriterier
##### Korrekthed
Klassediagrammet skal præcist afspejle de associationer, attributter og arveforhold, der er relevante for systemet.
##### Konsistens
Diagrammet skal stemme overens med domænemodellen og andre UML-diagrammer som sekvensdiagrammer.
##### Vedligeholdelse
Diagrammet skal være enkelt nok til at blive vedligeholdt, når krav ændrer sig.

---

## Relationships
#### Association
Broad term that describes any logical connection or relationship between classes.
![[Association.png]]

---

#### Directed Association
Directional relationship 
The airplane contains passengers.

![[Direted Association.png]]

---

#### Reflexive Association
Occrus when a class has multiple functions or responsibilities.
For example a staff member working in an airport may be a pilot, engineer, maintenence crew.
If the maintenence crew member is managed by the engineer. There could be managed relationship between 2 instances of the same class.

![[Reflexive Association.png]]

---

#### Multiplicity
Shows the number of elements in relation to the classes
An airplane may contain zero to many passengers.

![[Multiplicity.png]]

---

#### Aggregation
Refers to when a particular class is being built by a collection of instances of another class.
The contained classes are not strongly dependant on the lifecycle of the container
A library is made up of one or more books
But a book will remain so even when the library is dissolved.

![[Aggregation.png]]

---

#### Composition
Same as [[#Aggregation|Aggregation]] but with dependence of the contained class to the lyifecycle of the container class.
The contained class will be destroyed if the container class is destroyed.

![[Composition.png]]

---

#### Inheritance
Se [[Nedarvning|inheritance]]
Arrow from the [[Nedarvning#Derived class|child class]] to the [[Nedarvning#Base class|parent class]].

![[Inheritance UML.png]]

---

#### Realization/Interface
Se [[000 Bergrebsliste#Interface|Interface]]
The Printer Setup interface is being implemented by the Printer class.

![[Interface UML.png]]

---

## Example
![[TheMovies-DCD1.png]]
Bemærk at eksempel er både et DCD og et [[Package Diagram]] i ét.