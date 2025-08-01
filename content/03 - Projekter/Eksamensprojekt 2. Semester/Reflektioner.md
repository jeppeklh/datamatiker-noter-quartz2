
Transactions vs. triggers
Vi har valgt at bruge transactions frem for triggers, fordi transactions giver os mere kontrol over, hvordan logikken håndteres i applikationen. Triggers gemmer logik i selve datasen, hvilket kan gøre det sværere at gennemskue, hvor og hvornår bestemte handlinger udføres. Dette kan gøre debugging mere komplekst og kan føre til uhensigtsmæssige kædeoperationer, når triggers trigger andre triggers.


Commands inline eller i metoder.
Vi valgte at primært at implementere Comands inline for at holde koden kompakt. Denne tilgang gør logikken for den enkelte Command synlig direkte i konteksten og reducerer antallet af små fragmenterede metoder i ViewModelen.
I DCDét noterede vi Commands som metoder, da det bedre repræsenterer deres funktionelle karakter, end som properties. Selvom opsplitning i metoder kan gøre logikken mere genbrugelig og let at isolere, vurderede vi, at inline Commands var tilstrækkelige, da de var knyttet til specifikke funktioner.




At arbejde med et projekt af denne størrelse har givet os mulighed for at reflektere over vigtigheden af at vælge de rigtige teknologier og metoder til forskellige problemstillinger. I fremtidige projekter kunne vi med fordel fortsætte med at udforske anvendelsen af tråde og processer, især hvis systemet skal kunne håndtere øget belastning eller parallelisering af opgaver.


