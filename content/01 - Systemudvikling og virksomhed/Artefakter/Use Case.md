tags: #Systemudvikling #Artifact
> [!tldr] Definition
> En lille tekst, der beskriver hvordan systemet skal agere I bestemte situationer (men uden at fortælle hvordan systemet gør det)
>
> [[applying-uml-and-patterns-3rd.pdf#page=115&selection=0,11,0,20|Larman Kapitel 6]]

Aktøren udfører altid en Use Case
Kan have flere aktører

Man behøver ikke altid en fully dressed Use Case
Man behøver heller ikke altid en brief Use Case
Eller en casual Use Case
Det er case by case (hehe)

---

## Retningslinjer
##### Skriv i en essentiel, UI-fri stil 
Beskriv kun den grundlæggende opførsel og undgå at specificere brugergrænsefladen. Dette gør use cases nemmere at vedligeholde og mere fleksible i forhold til ændringer i grænsefladen.

##### Skriv korte og præcise use cases
Gør dem lette at forstå og ikke for detaljerede. Larman foreslår at bruge en ”fully dressed” stil i visse situationer, men ofte vil en kort version være tilstrækkelig.

##### Skriv black-box use cases
Beskriv kun, hvad systemet skal gøre, set udefra (i en black-box stil). Undgå at nævne interne detaljer om systemets implementering.

##### Tag aktør- og målperspektivet
Beskriv use cases med fokus på aktørens mål og systemets reaktion.

##### Find use cases gennem aktørers mål
Brug aktørers mål som udgangspunkt for at identificere use cases.

##### Brug testkriterier til at finde nyttige use cases
Spørg, hvad der ville være et succesfuldt resultat af hver use case, for at hjælpe med at definere dem klart.

---

## Kvalitetskriterier
##### Forståelighed
Use cases skal være skrevet på en måde, der gør dem lette at forstå for både tekniske og ikke-tekniske interessenter.

##### Korrekthed
Beskrivelserne skal afspejle de faktiske krav korrekt. 

##### Konsistens 
Alle use cases skal være i overensstemmelse med kravspecifikationer og andre artefakter, såsom domænemodeller.

---

## Tests
Use Cases can be at different levels depending on the system boundary, actos, and goals.
What is a useful level to express use cases for application requirements analysis?
There are severeal rules of thumb including: 
- [[#The Boss Test|The Boss Test]]
- [[#The EBP Test|The EBP Test]]
- [[#The Size Test|The Size Test]]

---

#### The Boss Test
Your boss asks, "What have you been doing all day?" 
You reply: "Logging in!" 
Is your boss happy? 
If not, the use case fails the Boss Test, which implies it is not strongly related to achieving results of measurable value.


Boss-Test-failing use cases should not always be ignored. User authentication may fail the boss test, but can be important. 
([[applying-uml-and-patterns-3rd.pdf#page=155&selection=20,0,20,13&color=yellow|Larman p.155]])

---

#### The EBP Test
Elementary Buisness Process (EBP)
A task performed by one person in one place at one time.

Shouldn't be taken too literally. Could be a scenario with about five or ten steps. But it does not take days and multiple sessions.
Between a few minutes and an hour in length.
([[applying-uml-and-patterns-3rd.pdf#page=155&selection=29,0,29,12&color=yellow|Larman p.155]])

---

#### The Size Test
A use case is rarely a single action or step. It typically contains many steps.
A common mistake is to define just a single step within a series of related steps as a use case by itself.
Example: *Enter an Item ID* 
([[applying-uml-and-patterns-3rd.pdf#page=156&selection=13,0,13,13&color=yellow|Larman p.156]])

---

#### Example: Applying the Tests
##### Negotiate a Supplier Contract
Much broader and longer than an EBP. Could be modelled as a buisness use case rather than a system use case.

##### Handle Returns
Ok with the boss. Seems like an EBP. Size is good.

##### Log In 
Boss not happy if this is all you do all day!

##### Move Piece on Game Board
Single step - Fails the size stest.

([[applying-uml-and-patterns-3rd.pdf#page=156&selection=25,0,25,27&color=yellow|Larman p.156]])


