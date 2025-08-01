tags: #C-sharp #Programmering

## Definition 
---
En databasemodel er en datamodel, der viser [[Data|data]], som skal persisteres et sted.

Databasemodellen indeholder UML-klasser som et [[Design Class Diagram|DCD]], men UML-klasserne repræsenterer nu hver for sig en [[Relationer|relation]]/[[Table|tabel]] i [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|databasen]] og ikke en softwareklasse.

Hver UML-klasse (dvs. en relation/tabel) indehol­der attributter, men hvor hver attribut nu repræsenterer en kolonne og ikke et [[Fields|felt]] eller [[Properties|property]] som i DCD’et. 

På samme måde som i DCD’et angives der også en [[Datatypes|datatype]] efter et attributnavn adskilt med semikolon. Forskellen er, at der nu angives [[SQL Data Types|SQL-datatyper]] i attributten og ikke C#/.NET-datatyper eller lignende.

Databasemodellen skal være så tilstrækkelig udfyldt, at en anden udeforstående kan implementere modellen fyldestgørende i et [[R-DBMS|R-DBMS]].

## Example
---
Vi tager først udgangspunkt i det simple relationsskema for SEMESTER:

SEMESTER (<u>SemesterId</u>, Number)

![[Databasemodel eksempel 1.png]]

PARTICIPANT (<u>Email</u>, FirstName, LastName, ImagePath, <span class="red">*SemesterId*</span>)
![[Databasemodel eksempel 2.png]]

Vi fortsætter for hele [[Databaseskema|databaseskemaet]]:

SEMESTER (<u>SemesterId</u>, Number)  
SUBJECT (<u>SubjectId</u>, Title, <span class="red">*SemesterId*</span>)  
PARTICIPANT (<u>Email</u>, FirstName, LastName, ImagePath, <span class="red">*SemesterId*</span>)  
LESSON (<u>LessonId</u>, Date, <span class="red">*SubjectId*</span>)  
PARTICIPANT_LESSON (<span class="red"><u>*Email*</u></span>, <span class="red"><u>*LessonId*</u></span>)  
TEACHER (<span class="red"><u>*Email*</u></span>, <span class="red">*SubjectId*</span>)  
STUDENT (<span class="red"><u>*Email*</u></span>, Badge)

![[Databasemodel eksempel 3.png]]

- I UML-klassen for tabellen PARTICIPANT_LESSON (som nedbryder en M:M-association til to 1:M-associationer) er stereotypen «PK» angivet for hver af de to kolonner Email og LessonId, der som sammensat nøgle er tabellens primærnøgle. Kolonnerne Email og LessonId er samtidig hver for sig fremmednøgler til tabellerne PARTICIPANT henholdsvis LESSON angivet med «FK1» henholds­vis «FK2» for tydeliggøre to helt forskellige fremmednøgler. Var de to kolonner en sammensat fremmednøgle, ville det have været tilstrækkeligt bare at angive «FK» for begge kolonner.

- Tabellen TEACHER har også to forskellige fremmednøgler angivet med «FK1» og «FK2»
- Email-kolonnen i tabellerne PARTICIPANT, TEACHER og STUDENT fungerer alle tre steder som primærnøgle jf. 1. alternativ i afbildning af nedarvning (generalisering/specialisering)



Når man angiver en [[Restriktion|restriktion]] i UML-databasemodellen, så kan man benytte i ny sektion i ’tabel’-klassen under attributterne (svarende til operationer i en softwareklasse i et DCD). Her vil man typisk navngive en restriktion samt angive, hvilke kolonner i tabellen indgår i restriktionen.


Hvis vi fortsætter med at tilføje associationer,multiplicitet og restriktioner.
![[Databasemodel eksempel 4.png]]





## Related Topics
---
- Link
- 

## Resources
---
- Link
- 