## Genopfrisk
---
Denne opgave er tænkt som en rolig opstart primært med praktisk repetition af udvalgte emner fra 1. semester. Du genopfrisker de emner, du selv vurderer, du skal styrkes i, dog sørg for som minimum at sættes dig ind i The Movies-casen.

Formålet med dagens opgave er at få startet godt ud med casen The Movies. I skal arbejde med den over de næste tre uger, og I skal arbejde i sprints og få berørt de fokusområder, der er beskrevet i casen i hvert sprint.

## Øvelse 1 - The Movies
---
#### Planlægning
---
Første opgave er at få lavet en realistisk plan.

##### Krav til planlægningsfasen:
· Èn uge til hvert sprint
· Èt scenarie i hvert sprint

#### High Level Design
---
I har nu lavet et plan og skal i gang med første sprint og udarbejdelse af The Movies analyseartefakter.

##### Krav til HLD-fasen:
· Beskriv systemet med de nødvendige artefakter inden for HLD.
· Lav dem kun på det skridt, du er i gang med

#### Low Level Design
---
Lav de nødvendige artefakter inden for LLD.

##### Krav til designfasen:
· Beskriv en lagdelt arkitektur via et pakkediagram (kun med lag, klassenavne og afhængigheder), hvor der er krav om, at MVVM-arkitekturmønstret skal anvendes i en WPF-applikation.

· Udarbejd en DCD med de klasser (med klassenavne, attributter og operationer), som relevante for use casen. Undgå at have alle domæneklasser med, men overhold et krav om, at DCD’et skal indeholde mindst én View-klasse, mindst én ViewModel-klasse, mindst én Repository-klasse og mindst én Model-klasse, så alle typer er repræsenteret.

· Udarbejd en SD for en udvalgt operationskontrakt, hvor kravet er, at SD’et tydeligt skal vise, hvordan den i SD’et beskrevne operation ændrer systemets tilstand fra kontraktens præ-betingelse (en: precondition) til dets post-betingelse (en: postcondition).

· Planlæg persistens i CSV-tekstfiler med relevant syntaks. Det skal være en Repository-klasse, som har ansvaret for at persistere. Sørg for enten, at I kan læse data fra en CSV-fil ind i it-systemet eller skrive data til en CSV-fil; gerne begge dele, hvis der er tid. Husk at holde det simpelt og vælg det letteste først. Benyt gerne data fra den udleverede CSV-fil.

· Design en WPF-brugergrænseflade med ét hovedvindue samt en dialogboks til indtastning af data; igen hold det simpelt via XAML. Der må gerne bruges databinding mellem View-laget og ViewModel-laget.

#### Programmering
---
Lav implementeringen ud fra HLD og LLD.

##### Udleveret CSV-fil med data

Der ligger et eksempel på konkrete data med både et regneark Uge33-TheMovies.xlsx og en CSV-fil Uge33-TheMovies.CSV, som har været anvendt til at registrere film, forestillinger og bookinger (det er de samme data i de to filer, bare med forskelligt format). Det står frit for, hvordan data i regnearket anvendes i både design- og implementeringsøjemed; du kan anvende det, som det er, eller supplere det med yderligere relevante data. Hele regnearket kan anvendes eller dele af det, som det passer dig og din gruppe bedst.

##### Krav til implementeringsfasen:
· Det er særdeles vigtigt, at du i denne fase får repeteret, hvordan man syntaktisk definerer en C#-klasse med dets 4 centrale medlemmer: fields, properties, constructors og methods, herunder også hvordan man implementerer de fire OOP-principper indkapsling, polymorfi, nedarvning og abstraktion i en C#-klasse.

· **VIGTIGT**: I den iterative proces, sørg for, at hver i din gruppe for mulighed for at lave en C#-klasse uanset hvilken type, det er; så husk at uddelegere opgaven.

#### Test
---
Udfør de planlagte tests.

##### Krav til testfasen:
· Testning af SD for en udvalgt operationskontrakt.
  **Eksempel:**
  Lad os antage, at operationskontrakten handler om at tilføje en ny film til systemet. Så du har flere testcases såsom “tilføj en gyldig film”, “tilføj en film uden titel”, osv.

· Testning af persistens i CSV-tekstfiler.
  Testcases kan være “læs data fra CSV-filen”, “skriv data til CSV-filen", osv.

· Prøv selv at finde på ny testcases, især hvis du har udvalget andre operationskontrakter end tilføj film, men i alle omstændigheder testning af persistens skal implementeres.




Hav fokus på at få ”hul” igennem fra en brugergrænseflade til persisteret data i en CSV-fil, dvs. en forbindelse gennem alle lag. Opgaven repræsenterer et ultrakort sprint, så start simpelt, f.eks. med at vise alle film fra en CSV-fil, eller noget tilsvarende.

God fornøjelse!