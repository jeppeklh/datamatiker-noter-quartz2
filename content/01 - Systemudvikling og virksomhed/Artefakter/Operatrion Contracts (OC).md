tags: #Systemudvikling #Artifact
## Definition
---
[[applying-uml-and-patterns-3rd.pdf#page=286&selection=0,11,0,31|Larman kapitel 11]]

En operationskontrakt (OC) er et artefakt i [[Unified Process]] (UP), der anvendes til at beskrive systemoperationer i detaljer. 

Selvom [[Use Case|use cases]] generelt er tilstrækkelige til at beskrive systemets opførsel, kan operationskontrakter være værdifulde til at specificere komplekse og subtile operationer mere præcist. 

Operationskontrakter fokuserer på de tilstandsændringer, der sker i [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|domænemodellens]] objekter som et resultat af operationen.
([[applying-uml-and-patterns-3rd.pdf#page=287&selection=4,1,5,53|Larman p.287]])

Operationskontrakter udarbejdes typisk under elaboration-fasen i UP, når man arbejder med at detaljere use cases og analysere systemoperationer. 
([[applying-uml-and-patterns-3rd.pdf#page=305&selection=26,1,33,90|Larman p.305]])
De er dog ikke et krav, men et værktøj, man kan vælge at bruge, når det giver mening for at forbedre forståelsen af systemet.
### Opbygning
---
En operationskontrakt består typisk af følgende sektioner:
([[applying-uml-and-patterns-3rd.pdf#page=290&selection=0,6,0,54|Larman p.290]])
**Operation**: 
Navnet på operationen og dens parametre.

**Krydsreferencer**: 
Hvilke [[Use Case|use cases]] operationen kan forekomme i.

**Forudsætninger**: 
Væsentlige antagelser om systemets tilstand eller objekterne i [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|domænemodellen]], før operationen udføres. Det er vigtigt at nævne ikke-trivielle antagelser, som læseren bør være opmærksom på.

**Efterbetingelser**: 
Beskriver ændringerne i objekterne i domænemodellen efter operationen er udført. Dette er den vigtigste del af kontrakten.

## Relation til SSD
---
Operationskontrakter defineres for systemoperationer, som er de operationer, systemet tilbyder i sin offentlige grænseflade. 

Systemoperationer identificeres typisk ved at bruge [[System Sequence Diagram (SSD)]], som viser interaktionen mellem eksterne aktører og systemet. 

SSD'er er nyttige til at visualisere de systemhændelser, som aktørerne genererer, og til at forstå rækkefølgen af disse hændelser.


## Hvordan de laves
---
[[applying-uml-and-patterns-3rd.pdf#page=298&selection=0,1,14,30|Larman p.298]]
Identify system operations from the SSDs.

1. For system operations that are complex and perhaps subtle in their results, or which are not clear in the use case, construct a contract.

2. To describe the postconditions, use the following categories:

	- instance creation and deletion
	
	- attribute modification
	
	- associations formed and broken

3. Writing Contracts

	As mentioned, write the postconditions in a declarative, passive past tense form (was …) to emphasize the observation of a change rather than a design of how it is going to be achieved. For example:
	
	(better) A SalesLineItem was created.
	
	(worse) Create a SalesLineItem.


## Hvorfor OC
---
Fordele ved at Bruge Operationskontrakter

**Præcision**: 
Operationskontrakter giver en mere detaljeret og præcis beskrivelse af en systemoperations effekt på [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|domænemodellen]], end man typisk finder i [[Use Case|use cases]].

**Fokus på Analyse**:
Kontraktformatet hjælper med at adskille beskrivelsen af systemets funktionalitet (hvad der skal ske) fra implementeringen (hvordan det skal ske).

**Dokumentation**:
Operationskontrakter fungerer som dokumentation af systemets adfærd, hvilket kan være nyttigt for udviklere og andre interessenter.

Det er ikke nødvendigt at skrive operationskontrakter for alle systemoperationer.

Man bør fokusere på de operationer, der er komplekse, subtile eller ikke fuldt ud beskrevet i use cases. 
([[applying-uml-and-patterns-3rd.pdf#page=298&selection=6,1,7,44|Larman p.298]])

Hvis udviklerne nemt kan forstå, hvad der skal ske uden operationskontrakter, bør man undlade at skrive dem.
([[applying-uml-and-patterns-3rd.pdf#page=297&selection=19,0,19,95|Larman p.297]])
## Kvalitetskriterier
---
#### Er
- Sikre sig at attributterne i operationen er i overensstemmelse med attributterne i domænemodellen
- Sikre sig at operationen er tilstede i [[System Sequence Diagram (SSD)|SSD'en]]
#### Er ikke!
- Sikre sig at postcondition er tilstede i [[System Sequence Diagram (SSD)|SSD'en]] (læg mærke til [[System Sequence Diagram (SSD)|SSD]], ikke [[Operatrion Contracts (OC)|OC]])
- Sikre sig at preconditions er tilstede i  [[System Sequence Diagram (SSD)|SSD'en]] (ditto)
- Sikre sig operations navnet er i overenstemmelse med C# kode konventioner
- Sikre sig at operations navnet er på engelsk

## Eksempler på typer af posconditions
---
> ([[applying-uml-and-patterns-3rd.pdf#page=292&selection=0,0,0,32&color=yellow|p.292]])
> 11.4. Definition: Postconditions

#### Er 
- Instance creation
- association formed
- attribute modification
#### Er ikke!!
- class modification
- message sent


Tænk i forhorld til domænemodellen. association formed (associations er strergerne i domænemodellen)

## Forbindelser til andre Artefakter
---
Operationskontrakter er relateret til andre artefakter i UP, f.eks.:

**SSDs**: 
SSD'er bruges til at identificere systemoperationer, som kan beskrives mere detaljeret i operationskontrakter.

**Glossary**: 
Glossaryen kan indeholde detaljerede beskrivelser af dataelementer, der nævnes i operationskontrakter.

**Domænemodel**: 
Operationskontrakter beskriver ændringer i tilstanden af objekter i domænemodellen.

**Use Case Model**: 
Operationskontrakter for systemniveauet er en del af Use-Case Modellen.
([[applying-uml-and-patterns-3rd.pdf#page=305&selection=11,0,17,30|Larman p.305]])
