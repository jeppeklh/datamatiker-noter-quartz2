---
aliases:
  - Functional Dependencies
---
tags: #Programmering #SQL

> [!tldr] Definition
> En constraint mellem 2 attributter.

Funktionelle afhængigheder er et grundlæggende begreb i [[Database Design|databasedesign]] og bruges til at etablere [[Relationer|relationer]] mellem attributter i et [[Relationsskema|relationsskema]]. De bruges til at sikre, at [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|databasen]] er i en [[Normalisering|normaliseringstilstand]], hvilket hjælper med at minimere [[Redundans|dataredundans]] og forbedre dataintegriteten.

En funktionel afhængighed beskriver en [[Relationer|relation]] mellem attributter i en [[Table|tabel]]. Hvis attribut X funktionelt bestemmer attribut Y, betyder det, at for hver værdi af X er der præcis én værdi af Y.   
  
Det er betegnet som   
X → Y  
hvor attributten sat på venstre side af pilen, X kaldes Determinant (_Determinant_ ), og Y kaldes afhængig (_Dependent_).

Det er vigtigt at bemærke, at funktionelle afhængigheder kun gælder for de enkelte tuples (rækker) i tabellen, og ikke for tabellen som helhed

---

## Example
I en database med studerende, vil **Student_ID** (determinant) bestemme den studerendes navn, adresse og andre personlige oplysninger (afhængig). 

Det betyder, at vi med et **Student_ID** kan bestemme den tilsvarende studerendes navn og andre personlige oplysninger, men ikke omvendt.

**Student_ID** → Name, Contact, College, etc.

## Example 2

|   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|
|**Student_ID**|**Name**|**Contact**|**College**|**Course**|**Teacher**|**Rank**|
|100|Jens|73009348|UCL|Programming|Thomas|2|
|100|Jens|73009348|UCL|Systemudvikling|Lene|2|
|102|Patrick|73009015|UCL|Programming|Thomas|2|
|103|Pia|73009367|UCL|Programming|Thomas|2|


**Afhængigheder i Eksemplet**

**Student_ID** → Name  
**Student_ID** → Contact  
**Student_ID** → College  
**College** → Rank  
**Course** → Teacher  
****Student_ID,** **Course**** → Teacher

Derfor (Givet StudentID og Course kan man determinere de andre.):  
****Student_ID,** **Course**** → Name, Contact, College, Rank, Teacher


En mere udpenslet:
- **Student_ID → Name, Contact, College**
    - Given a `Student_ID`, you can uniquely determine the `Name`, `Contact`, and `College` of the student.
- **College → Rank**
    - Given a `College`, you can uniquely determine the `Rank` of that college.
- **(Student_ID, Course) → Teacher**
    - Given a combination of `Student_ID` and `Course`, you can uniquely determine the `Teacher`.
- **(Course, College) → Teacher**
    - Given a `Course` and `College`, you can uniquely determine the `Teacher`

---

**(Student_ID, Course) → Name, Contact, College, Rank, Teacher**

**is correct** because:

- `Student_ID` determines `Name`, `Contact`, and `College`.
- `Student_ID` (through `College`) determines `Rank` (transitive dependency).
- The combination of `Student_ID` and `Course` determines the `Teacher`.

---

## Typer

### Fuld funktionel afhængihed
Her bestemmer en attribut eller et sæt attributter entydigt en anden attribut eller et sæt attributter. 

Hvis en relation R har attributterne X, Y, Z med afhængighederne **X → Y** og **X → Z**, hvilket angiver, at disse afhængigheder er fuldt funktionelle.  

For eksempel i databasen over studerende bestemmer Student_ID fuldt ud studerendes navn, adresse og andre personlige oplysninger.

---

### Delvis funktionel afhængighed
Her afhænger en ikke-nøgleattribut af en del af den [[Composite key| sammensatte nøgle]] end hele nøglen. 

Hvis en relation R har attributterne X, Y, Z, hvor X og Y er den sammensatte nøgle, og Z er ikke-nøgleattribut. Så er **X → Z** en delvis funktionel afhængighed i R-DMS.

I vores eksempel kan du se, at Student_ID alene ikke bestemmer hvem underviser et fag. 
På andre ord, primærnøglen i denne tabel er sammensat nøgle af Student_ID og Course. 
Denne sammensat nøgle er nu determinant. 
Men Teacher er kun afhængig af Course (en del af nøgleattribut), derfor denne afhængighed er en delvis funktionel afhængighed.

---

### Transitiv funktionel afhængighed
Her  er en afhængig attribut indirekte afhængig af determinanten. dvs. hvis a → b & b → c, så a → c og dette er en transitiv funktionel afhængighed.

I vores eksempel:  
**Student_ID** → College  
**College** → Rank

Så **Student_ID → Rank**
![[Transitiv afhængihed definition.png]]

---

## Anvendelse
### Identificér og eliminer [[Redundans|dataredundans]]
Hvis en [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] indeholder en tabel med attributter "Student_ID" og "Name", og en anden [[Table|tabel]] med attributter "Student_ID" og "Address", så er der en funktionel afhængighed mellem "Student_ID" og "Name" i den første tabel og mellem "Student_ID" og "Address" i den anden tabel.  
  
Ved at kombinere disse to tabeller til én, med attributter "Student_ID", "Name" og "Address", elimineres [[Redundans|dataredundans]].

---

### Identificér og fjern datainkonsistens
Vi tage den samme eksempel ovenfor. Hvis attribut Name ændres i den første tabel, men ikke i den anden tabel, er dataene inkonsistente.  
  
Ved at kombinere disse to tabeller til én  med attributter "Student_ID", "Name" og "Address", elimineres datainkonsistens.

---

## Related Topics
- Link
- 

---

## Resources
- Link
- 