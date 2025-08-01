---
aliases:
  - restriktion
  - Constraint
  - constraint
  - Constraints
  - constraints
---
tags: #Programmering #SQL

## Definition 
---
[[PRIMARY KEY|Primærnøgler]] og [[FOREIGN KEY|fremmednøgler]] er begge to eksempler på en restriktion, som i database-terminologi og i SQL betegnes ’constraint’ på engelsk. 

Vi har lige nu kun fokus på disse to typer af restriktioner, men der er også andre former for restriktioner (f.eks. index, trigger, unique, check), som vi ser på senere.
## Syntax
---
 «PK»-stereotypen først, at der er tale om en primærnøgle-restriktion og dernæst følger navnet på restriktionen.

Navngivningskonvention for primærnøgle-restriktionen er her valgt til at starte med ’PK_’ efterfulgt af navnet på tabellen ’Semester’ (UpperCamelCase).
![[Contraint example 1.png]]


 Restriktionen for fremmednøglen er angivet først med «FK»-stereotypen (evt. med «FK1», «FK2») for tilkendegive restriktionstypen, dernæst med restriktions­navnet ’FK_Participant_Semester’ opbygget med formatet FK_{fra-tabel}_ {til-tabel}, dvs. fremmednøglen refererer fra PARTICIPANT-tabellen til SEMESTER-tabellen, og tilsidst i parentes den kolonne (eller de kolonner), der indgår i primærnøglen i den refererede tabel, dvs. her ’SemesterId’ i SEMESTER-tabellen.

![[Constraint example 2.png]]



## Related Topics
---
- Link
- 

## Resources
---
- Link
- 