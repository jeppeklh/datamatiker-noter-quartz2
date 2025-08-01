tags: #Programmering #SQL

## Definition 
---
Et relationsskema (en: relation schema) beskriver en [[Relationer|relation]] og dets kolonner via et bestemt tekstformat:

**Relationsnavn (Kolonne-1, Kolonne-2, …, Kolonne-n)**

Selvom et relationsskema reelt set kun er en simpel tekstuel måde at angive en konceptuel klasse i [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|domæne­modellen]] som en [[Relationer|relation]], så er den også et mere praktisk format til at beskrive den trinvise transformation og justering, relationsskemaer gennemgår, når også nøgler introduceres til at repræsentere sammenhænge mellem klasser (asso­ciationer mm.).
## Example
---
PRODUCT (Name, Type, Color, Price)
## Navngivningskonvention for relationsskemaer
---
- **Relationsnavnet angives**:
    - singulært (i ental) (dvs. ’SEMESTER’) og aldrig pluralt (i flertal) (dvs. aldrig ’SEMESTERS’)
    - altid med store bogstaver (UPPERCASE) og undgå mellemrum
    - kun på engelsk, da et relationsskema er et LLD-artefakt
    - hvis relationsnavnet er en kombination af to eller flere ord, da separeres ordene med et underscore, f.eks. ’PARTICIPANT_LESSON’
- **Kolonnenavnet**:
    - starter med stort bogstav, derefter små bogstaver (UpperCamelCase): ( Email, FirstName, LastName, Image )
    - undgå mellemrum
    - angives kun på engelsk


## Primærnøglen
---
I et **relationsskema** er [[PRIMARY KEY|primærnøglen]] fremhævet ved at  
understrege kolonnen (eller de kolonner), der indgår i den.  
[[PRIMARY KEY|Primærnøglens]] kolonne(r) placeres traditionelt først i kolonnelisten.

LESSON (<u>LessonId</u>, Date, Subject

## Fremmednøglen
---
I et relationsskema er hver [[FOREIGN KEY|fremmednøgle]] fremhævet ved at  
kursivere skrifttypen for kolonnen (eller kolonnerne), der udgør fremmednøglen.  
Fremmednøgler placeres traditionelt sidst i kolonnelisten.


## Multiplicitetstyper
---
### 1:M
---
Hvis multipliciteten er en-til-mange (1:M) mellem to klasser i domænemodellen, da skal primærnøglen fra ’1’-tabellen kopieres til ’M’-tabellen som fremmednøgle.

I tilstedeværelse-eksemplet tages med fokus på 1:M-associationen mellem klasserne Semester og Deltager udgangspunkt i de to tilsvarende relationsskemaer SEMESTER og PARTICIPANT:
 
SEMESTER (<u>SemesterId</u>, Number)  
PARTICIPANT (<u>Email</u>, FirstName, LastName, Image)

For at repræsentere 1:M sammenhængen mellem semestre og deres deltagere (en deltager studerer kun under ét semester, men et semester kan have mange deltagere), da skal primærnøgle fra SEMESTER (dvs. SemesterId) kopieres til PARTICIPANT som en fremmednøgle (angivet i *kursiv* og med <span class="red">rødt</span>):

SEMESTER (<u>SemesterId</u>, Number)  
PARTICIPANT (<u>Email</u>, FirstName, LastName, Image, <span class="red">*SemesterId*</span>)

Hermed er 1:M-associationen repræsenteret korrekt i relationsskemaet.

### M:M
---  
I tilstedeværelse-eksemplet tages med fokus på M:M-relationen mellem klasserne Deltager og Lektion udgangspunkt i de to tilsvarende [[Relationsskema|relationsskemaer]] PARTICIPANT og LESSON:

PARTICIPANT (<u>Email</u>, FirstName, LastName, Image, <span class="red">*SemesterId*</span>)  
LESSON (<u>LessonId</u>, Date, Subject)

For at repræsentere M:M-associationen (en deltager kan deltage i mange lektioner, og en lektion kan have mange deltagere) skabes en helt ny link-[[Relationer|relation]] med et kombineret navn, samt [[PRIMARY KEY|primærnøgler]] fra PARTICIPANT og LESSON som [[FOREIGN KEY|fremmednøgler]]:

PARTICIPANT_LESSON (<span class="red">*Email*</span>, <span class="red">*LessonId*</span>)

I link-relationen er Email således en [[FOREIGN KEY|fremmednøgle]] ind i PARTICIPANT-[[Relationer|relationen]] og LessonId en [[FOREIGN KEY|fremmednøgle]] ind i LESSON-[[Relationer|relationen]].

Samtidig danner de to [[FOREIGN KEY|fremmednøgler]] tilsammen en sammensat [[PRIMARY KEY|primærnøgle]] for selve link-[[Relationer|relationen]]. Dette vises med en samlet understregning af begge:

PARTICIPANT_LESSON (<span class="red"><u>*Email*</u></span>, <span class="red"><u>*LessonId*</u></span>)

Bemærk, at der skal faktisk oprettes en ny [[Relationer|relation]], som ikke direkte kommer fra en klasse i domænemodellen, men i stedet repræsen­terer M:M-associationen mellem to klasser. 


Hermed er M:M-associationen korrekt repræsenteret i et relationsskema for link-relationen.
### 1:1
---
Hvis multipliciteten er en-til-en (1:1) mellem to klasser i domænemodellen, kan du frit vælge, hvilken tabel skal indeholde primærnøglen for den anden.

Tag følgende eksempel med de to [[Relationsskema|relationsskemaer]].

PERSON (<u>CprNumber</u>, Name, Address)

PASSPORT (<u>PassportNumber</u>, IssueDate, ValidToDate)

Man kan vælge at repræsentere 1:1 sammenhængen mellem de to [[Relationer]] ved at kopiere [[PRIMARY KEY|primærnøglen]] fra PERSON (dvs. CprNumber) ind i PASSPORT-relationen som en [[FOREIGN KEY|fremmednøgle]]:

PERSON (<u>CprNumber</u>,, Name, Address)

PASSPORT (<u>PassportNumber</u>, IssueDate, ValidToDate, <span class="red">*CprNumber*</span>)

Eller omvendt, kopiere [[PRIMARY KEY|primærnøglen]] fra PASSPORT (dvs. PassportNumber) ind i PERSON-[[Relationer|relationen]] som [[FOREIGN KEY|fremmednøgle]]:

PERSON (<u>CprNumber</u>,, Name, Address, <span class="red">*PassportNumber*</span>)

PASSPORT (<u>PassportNumber</u>, IssueDate, ValidToDate)

Normalt vil man faktisk ikke opretholde en 1:1-forbindelse mellem to [[Relationer]], men nærmere sammen­flette kolonnerne i de to relationer ind i én samlet [[Relationer|relation]]. Der kan dog være grunde til at holde de to [[Relationer]] adskilt, f.eks. sikkerhedsmæssige grunde, men det er ikke ofte, det sker.

## Afbildning af generalisering/specialisering (nedarvning) til relationsskemaer
---
Hvis [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|domænemodellen]] indeholder [[Nedarvning]] i form af generalisering/specialisering i domænemodellen, så kan afbildningen til relationsskemaer håndteres på tre forskellige alternative måder.

![[Domænemodel Eksempel (Database design).png]]
### 1. En Tabel for hver klasse
---
Tilgangen, der reflekterer domænemodellen bedst, er at oprette ét relationsskema for hver konceptuel klasse, der indgår i nedarvningsforholdet. Fra domænemodellen i figuren, fås da:

PARTICIPANT (<u>Email</u>, FirstName, LastName, Image, _SemesterId_)  
TEACHER (_SubjectId_)  
 STUDENT (Badge)

Dernæst skal primærnøglen for relationsskemaet, der repræsenterer superklassen, kopieres ned til relationsskemaerne for hver underklasser, så alle relationsskemaer i nedarvningsforbindelsen har den samme primærnøgle (samme sæt af kolonner).

Dvs. primærnøglen Email i PARTICIPANT kopieres ned til relationsskemaerne TEACHER og STUDENT:

PARTICIPANT (<u>Email</u>, FirstName, LastName, Image, <span class="red">*SemesterId*</span>)  
TEACHER (<u>Email</u>, <span class="red">*SubjectId*</span>)  
STUDENT (<u>Email</u>, Badge)

Derudover skal den nye primærnøgle i hver af relationsskemaerne, der repræsenterer underklasserne (specialiseringer) i domænemodellen, samtidig være fremmednøgler til relationsskemaet PARTICIPANT, der repræsenterer deres superklasse (generalisering) i domænemodellen.

  

I eksemplet ændrer dette relationsskemaerne TEACHER og STUDENT til følgende, hvor Email-kolonnen nu også er fremmednøgle begge steder:

  

PARTICIPANT (<u>Email</u>, FirstName, LastName, Image, <span class="red">*SemesterId*</span>)  
TEACHER (<span class="red"><u>*Email*</u></span>, <span class="red">*SubjectId*</span>)  
STUDENT (<span class="red"><u>*Email*</u></span>, Badge)

  

På denne måde er det sikret, at man kan kombinere information fra alle involverede relationer i f.eks. en forespørgsel til databasen. Dvs. en given række i TEACHER (eller STUDENT) kan kombineres med en række fra PARTICIPANT ved at benytte Email-kolonnen som fremmednøgle.

  

Bemærk specielt, at en kolonne både kan fungere  
som primærnøgle og fremmednøgle på samme tid.  
I dette tilfælde placeres kolonnen først i kolonnelisten.
### 2. Et Relationsskema for hver underklasse fra domænemodellen
---
Udgangspunktet i domænemodellen er som før: man har en nedarvningsforbindelse mellem en superklasse og flere underklasser. Det andet alternativ er nu, at man i stedet for at skabe relationsskemaer for alle involverede klasser kun skaber et relationsskema for hver underklasse i domænemodellen. Disse relations­skemaer får så yderligere information (kolonner) tilføjet fra superklassen.

Fra eksemplet med tilstedeværelse, vil dette resultere i de to relationsskemaer:

TEACHER_PARTICIPANT (<u>Email</u>, FirstName, LastName, Image, _SubjectId_, _SemesterId_)
STUDENT_PARTICIPANT (<u>Email</u>, Badge, FirstName, LastName, Image, _SemesterId_)

Bemærk at relationsnavnet er en kombination for at tydeliggøre hvor sammenfletningen kommer fra.

Dette alternativ vælges oftest, hvis superklassen har ganske få attributter og ikke indgår i mange andre sammenhænge.
### 3. Én Tabel
---
Man kan også modsat kombinere al information fra [[Nedarvning#Derived class|underklasserne]] ind i [[Nedarvning#Base class|superklassen]] i [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|domænemodellen]] ved at udtrykke dette i ét eneste relationsskema.

Fra eksemplet med tilstedeværelse, vil dette resultere i relationsskemaet:

PARTICIPANT (<u>Email</u>, FirstName, LastName, Image, Badge, <span class="red">*SubjectId*</span>, <span class="red">*SemesterId*</span>)

eller med relationsnavnet PARTICIPANT_TEACHER_STUDENT for at tydeliggøre sammenføringen:

PARTICIPANT_TEACHER_STUDENT (<u>Email</u>, FirstName, LastName, Image, Badge, <span class="red">*SubjectId*</span>, <span class="red">*SemesterId*</span>)

Nu kan man nemlig ikke ved hvad hver entitet er, er den Teacher eller Student, derfor tilføjes en ny kolonne til relationen til at identificere entitetenstype:

PARTICIPANT_TEACHER_STUDENT (<u>Email</u>, FirstName, LastName, Image, Badge, Type, <span class="red">*SubjectId*</span>, <span class="red">*SemesterId*</span>)

Dette alternativ vælges oftest, hvis underklasserne har få attributter og ikke indgår i mange sammen­hænge, og vil have konsekvensen, at mange rækker ville indeholde en null-værdi (dvs. ingen værdi) for SubjectId-kolonnen og Badge-kolonnen afhængig af, hvilken type rækken repræsenterer. Med andre ord en række, der repræsenterer en deltager af typen ’underviser’, vil have null-værdier for Badge-kolonnen, da de kun er relevante for en studerende.
## Related Topics
---
- Link
- 

## Resources
---
- [Database design læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_6/scormcontent/index.html#/lessons/R-uiHxV6wOoSodZUwqhx474w15v28DWY)


![[Relationsskemaer fra domænemodel.png]]