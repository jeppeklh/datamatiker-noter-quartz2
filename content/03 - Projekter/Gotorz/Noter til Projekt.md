Flight and hotel merged together in one package


## Problems
---
- Price changes day to day. It need to be checked everyday
- Availability of flight and hotel. Also needs to be checked often. Package needs to be deleted if one is not availabale
- Wasting time
- Exapanding

## New project idea
---
- Flights API 
- Hotels API

Get the flights data from flight API, and the hotels adata from the hotel API. Merge them in to a package, and then make the package ready.

APIs
Skyscanner


10% Markup

24 hours from booking to recieving tickets

## Spørgsmål
---

Procesmodel - Cyklisk Inkrementel

Projektstyring - ScrumBantt
- Gantt - Den generelle tidslinje, med 'deadlines'
- Kanban - Strukturen fra kanbanboard, WIP (for at undgå overarbejde fra enkelte personer) 
- SCRUM - Strukturen for SCRUM ceremonier (et daily møde - med codereviews, sprint planning), [[Definition of Done]]

GANTT kontra timeboxing

GANT eller burndowncharts.
Ville vi skulle lave Gant over hver feature eller også hvert task under hver feature.


Skal vi kalde projektstyring SCRUM som en del af det? 
Vi bruger kun SCRUM-ceremonier i form af strukturen og møder. De krav for de ceremonier lever vi ikke helt op til. 

Skal vi kalde Systemudvikling RAD eller Incremental Waterfall?. Der er mange ting fra RAD vi ikke bruger - Prototyper, 'Rapid-delen' (webudvikling er nyt os. Så det er fint nok med ting som længere kodereviews osv.)
Spørgsmålet er, om man kan kalde det RAD, når det er meget begrænset hvd vi bruger derfra.

Hvorfor blev vi anbefalet RAD og XP?  De kræver meget kontakt med kunde/stakeholder.

Komme ind på mønstre

Kigge en del på fokusområdet 'Test'
 - Høre efter når der bliver nævnt forskellige typer af test

SKRIV TEKNIKKERNE OP

 Det kan være men det kan være det kan 




I systemudvikling er jeg ved at sætte min projektstyringmetode op til min systemudvikling. Jeg vil have dig til at skrive teknikkerne op så i en rækkefølge der giver mening. Teknikkerne skal skrives som en enkelt sætning med aktivitet, input, og formål. Altså på formularen. Der skal laves.., baseret på.., for at/ med deet formål...

Altså formålet for den forhændværende teknik skal være inputtet i den den næste. Dette er for at skabe sporbarhed mellem teknikkerne. Husk at teknikkerne ikke er bestemte værktøjer eller modeller. Det er mere overordnet. Altså vi bruger bestemte værktøjer til at udføre teknikken. Her er mine noter til projektstyring:


Generelt hvordan skal vi skelne mellem systemudvikling og projektstyring?

Skal planning poker også være med oppe i Systemudviklingsmetoden. 

Planlægning i vores projekstyringmetoder er tilsvarende feature liste i vores systemudviklingsmodel, er det ok?

Og er en product backlog i grunden projekstyring eller systemudvikling?

Skal teknikker beskrives med aktivitet, input of formål i projekstyringmetoden?



Vi har ikke APIController fordi vi kalder direkte til en ekstern API. Vi laver ikke vores egne Endpoints. Få styr på Actionmedthods. 
Og forskellen mellem APIControllers og MVC controllers.

## Kommentarer til kode
---
RegisterCustomer og RegisterEmployee - Kig på Debouncing og cancellatiotokens osv. (Specifikt DebounceUsernameCheck).

