tags: #Systemudvikling #Artifact
> [!tldr] Definition
> En domænemodel er en af de vigtigste modeller inden for objektorienteret analyse. 
> Den illustrerer **væsentlige koncepter** i et domæne og kan fungere som inspiration til design af softwareobjekter.
>
> [[applying-uml-and-patterns-3rd.pdf#page=218&selection=0,11,0,24|Larman kapitel 9]]

Domænemodellen er en **visuel repræsentation af forretningskoncepter og deres relationer**, ligesom en ordbog, men med visuel støtte fra UML klassediagrammer.

Generel oversigt over, hvilke slags objekter der kan være I systemet.
Indeling af objekter I klasser og atributter. For at få en oversigt

---

## Hvad den bruges til
- Skaber et overblik over de [[Konceptuelle klasser]]
- Skaber en struktureret navngivning af domænets forretningsbegreber
- Viser sammenhængene mellem de konceptuelle klasser
- Sikrer sporbarhed til domænet
- Sikrer at man har forstået kundens beskrivelse af domænet (i samarbejde med kunden)

---

## Hvorfor er den vigtig
Domænemodellen er central, fordi den hjælper os med at **forstå forretningsdomænet** og **identificere de vigtigste elementer** i det. 2

Den fungerer som et **fælles sprog** for både udviklere og forretningseksperter, der sikrer en **fælles forståelse** af systemet. 1 
Denne fælles forståelse er afgørende for at udvikle et system, der opfylder brugernes behov.

Domænemodellen tjener som input til flere artefakter, der udforskes i casestudier, herunder design af softwareobjekter. 
([[applying-uml-and-patterns-3rd.pdf#page=219&selection=2,0,13,38|Larman p.219]])

---

## Retningslinjer
##### Undgå at blande attributter og klasser sammen
Hvis noget har sin egen identitet og opførsel, så modeller det som en klasse, ikke som en attribut.

> Guideline 
> If we do not think of some conceptual class X as a number or text in the real world, X is probably a conceptual class, not an attribute.
([[applying-uml-and-patterns-3rd.pdf#page=241&selection=7,0,10,49|Larman s. 241]])

##### Associationer
> ([[applying-uml-and-patterns-3rd.pdf#page=247&selection=22,0,27,55|Larman p.247]])
> Guideline Consider including the following associations in a domain model: Associations for which knowledge of the relationship needs to be preserved for some duration ("need-to-remember" associations). Associations derived from the Common Associations List.

Navngivning af associationer:
> ([[applying-uml-and-patterns-3rd.pdf#page=248&selection=21,0,28,63&color=yellow|Larman p.248]])
> Guideline Name an association based on a ClassName-VerbPhrase-ClassName format where the verb phrase creates a sequence that is readable and meaningful.

##### Ingen fremmednøgler som attributter
> ([[applying-uml-and-patterns-3rd.pdf#page=262&selection=40,0,40,50&color=yellow|Larman p.262]])
> Guideline: No Attributes Representing Foreign Keys

---

## Kvalitetskriterier
##### Korrekthed
Domænemodellen skal præcist afspejle de vigtige begreber og relationer fra problemdomænet.

##### Fuldstændighed
Domænemodellen skal indeholde alle væsentlige koncepter og relationer i domænet.
##### Konsistens
Alle koncepter og relationer i domænemodellen skal være i overensstemmelse med use cases og andre systemkrav. Skal være konsistent i sin brug af terminologi og notation.
([[applying-uml-and-patterns-3rd.pdf#page=198&selection=0,0,9,40|Larman p.198]])
##### Vedligeholdelse
Modellen skal være struktureret på en måde, så den kan opdateres efterhånden som systemet udvikler sig.

##### Abstraktion
Domænemodellen skal fokusere på forretningskoncepter og undgå tekniske detaljer, der hører til implementeringen.

---

## Ekstra
##### Find konceptuelle klasser
Identificer konceptuelle klasser i domænet, der repræsenterer vigtige ting eller begreber. Brug kilder som kravspecifikationer og use cases til at finde disse klasser.

##### Agil modellering
Skitsér domænemodeller hurtigt på et whiteboard og lav dem kun så detaljerede, som situationen kræver.

##### Opbevar modeller i værktøjer kun ved behov: 
Hvis projektet kræver formel dokumentation eller langvarig vedligeholdelse, kan det være nødvendigt at bruge værktøjer til at gemme modeller.

##### Brug domænespecifikke termer
Sørg for, at modellerne afspejler termer, der er brugt af forretningen eller kunderne.

##### Inkludér "beskrivelsesklasser" når relevant
Hvis der er behov for at holde styr på mange egenskaber om en klasse (f.eks. produkter), så brug en separat beskrivelsesklasse til dette.

---

## Sporbarhed
[[Repo/01 - Systemudvikling og virksomhed/Artefakter/Objektmodel|Objektmodellen]] skal altid afspejle Domænemodellen og omvendt

---

## Eksempel
![[Domænemodel.png]]
Man må godt skrive at den mange til mange relation bliver løst senere i dcd eller dartabsemodel som en sammesat klasse. 
eks: bruger og projekt, bliver til brugerprojekt. Dette er ikke en konceptuel klasse og skal ikke være i domænemodellen Det findes ikke i virkeligheden.

