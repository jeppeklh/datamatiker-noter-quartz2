
tags: #Programmering #SQL

## Definition 
---
Formålet med database design er at organisere [[Data|data]] på en måde, der opfylder brugernes behov, understøtter forretningsprocesser, og tillader fleksibel og effektiv adgang til [[Data|data]].
## Trinene i fase A – database-designfasen
---
![[Database Designproces.png]]




Disse designtrin starter med domæneforståelsen og resulterer i en UML-databasemodel for domænet:

1. Domæneforståelse etableres via [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|domænemodellen]].

2. Konceptuelle klasser i [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|domænemodellen]] konverteres til enkelte relationsskemaer

3. De relevante relationsskemaer samles til et relationelt databaseskema.

4. En UML-databasemodel (fasens slutprodukt) etableres ud fra relationsskemaerne samlet i det relationelle databaseskema i det forrige trin samt evt. fra [[Datatypes|datatype]]-information i [[Design Class Diagram|DCD]]’et konverteret til [[SQL Data Types|SQL-datatyper]]

Den resulterende UML-databasemodel indgår som input til [[Database Implementering|fase B]].
### Trin 1: Domæneforståelse etalberes via domænemodellen
---
Ændr sprog fra dansk([[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|Domænemodel]]) til engelsk


### Trin 2: Afbild konceptuelle klasser i [[Relationsskema|Relationsskemaer]]
---
[[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|Domænemodellens]] konceptuelle klasser repræsenterer en objekt-orienteret tilgang, hvor [[Data|data]] håndteres som objekter, hvorimod en [[R-DBMS|relationel database]] gemmer [[Data|data]] med en relationel tilgang i form af rækker i [[Relationer|relationer]] organiseret via [[Table|tabeller]], kolonner og rækker.

Som tidligere nævnt gemmer en relationel database sine data i tabeller, dvs. informationer om konkrete [[Entity|ting]] som udtryk for forretningsmæssige begreber i et domæne, og hjælper med at holde styr på disse.

At en relationel database gemmer data i tabeller er ikke helt korrekt; mere præcist gemmes data i form af [[Relationer]], som er en speciel type af tabel.

Deles op i 2 undertrin.
#### 1: Afbildning af konceptuel klasser og attributter
---
Først afbildes konceptuelle klasser og deres attributter fra domænemodellen til [[Relationsskema]]­ernes tekstuelle repræsentation.

**Hver konceptuel klasse i [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|domænemodellen]] afbildes som ét [[Relationsskema]],  
hvori klassens attributter afbildes som kolonner i skemaet**.
##### Eksempel

Domænemodel:
![[Domænemodel Eksempel (Database design).png]]
```SQL
SEMESTER (Number)
SUBJECT (Title)
PARTICIPANT (Email, FirstName, LastName, Image)
LESSON (Date)
TEACHER (Subject)
STUDENT (Badge)
```
#### 2: Afbildning af sammenhænge mellem konceptuel klasser
---
Dernæst afbildes sammenhænge (associationer mm.) mellem konceptuelle klasser i [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|domæne­modellen]] via justering af [[Relationsskema|relationsskemaer]] fra første undertrin med introduktion af nøgler mm

**Sammenhænge** mellem konceptuelle klasser i [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|domænemodellen]] udtrykkes:

- via **associationer** med **multipli­citeter**
- via **generalisering**/**specialisering** (knap så ofte forekommende)

Bemærk, at en association sagtens kan eksistere fra og til den samme klasse uden, at det nødvendigvis skal behandles som et specialtilfælde. Man ser det bare ikke så ofte.

##### Eksempel

Domænemodel:
![[Domænemodel Eksempel (Database design).png]]

Domænemodellen i figuren indeholder fire associationer med to typer af multiplicitet:

- En 1:M-association mellem Semester og Fag
- En 1:M-association mellem Semester og Deltager
- En 1:M-association mellem Fag og Lektion
- En M:M-association mellem Deltager og Lektion

Der er ingen 1:1-associationer i dette eksempel

Hver af de to [[Relationsskema#Multiplicitetstyper|multiplicitetstyper]] ([[Relationsskema#1 M|1:M]] og [[Relationsskema#M M|M:M]]) skal håndteres på forskellig vis, når associationen afbildes til relationsskemaer.

SEMESTER (<u>SemesterId</u>,Number)  
SUBJECT (<u>SubjectId</u>, Title,  <span class="red">*SemesterId*</span>)  
PARTICIPANT (<u>Email</u>, FirstName, LastName, Image, <span class="red">*SemesterId*</span>)  
LESSON (<u>LessonId</u>, Date, _SubjectId_)  
PARTICIPANT_LESSON (<span class="red"><u>*Email*, *LessonId*</u></span>)  
TEACHER (<u>Email</u>, <span class="red">*SubjectId*</span>)  
 STUDENT (<u>Email</u>, Badge)


## Trin 3: De relevante relationsskemaer samles til et relationelt databaseskema.
---
Vi samler nu vores [[Relationsskema|realtionsskemaer]] til et relationelt [[Databaseskema|databaseskema]].

SEMESTER (<u>SemesterId</u>, Number)  
SUBJECT (<u>SubjectId</u>, Title, <span class="red">*SemesterId*</span>)  
PARTICIPANT (<u>Email</u>, FirstName, LastName, ImagePath, <span class="red">*SemesterId*</span>)  
LESSON (<u>LessonId</u>, Date, <span class="red">*SubjectId*</span>)  
PARTICIPANT_LESSON (<span class="red"><u>*Email*</u></span>, <span class="red"><u>*LessonId*</u></span>)  
TEACHER (<span class="red"><u>*Email*</u></span>, <span class="red">*SubjectId*</span>)  
STUDENT (<span class="red"><u>*Email*</u></span>, Badge)

## Trin 4: En UML-databasemodel etableres ud fra det relationelle databaseskema
---
Vi kan nu lave en [[Databasemodel]]
![[Databasemodel eksempel 4.png]]
## Related Topics
---
- Link
- 

## Resources
---
- [Database Design læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_6/scormcontent/index.html#/lessons/R-uiHxV6wOoSodZUwqhx474w15v28DWY)
