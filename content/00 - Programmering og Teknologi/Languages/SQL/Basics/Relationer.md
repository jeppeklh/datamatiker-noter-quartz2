tags: #Programmering #SQL

> [!tldr] Definition
> **En** **relation** **er en todimensionel [[Table|tabel]] bestå­ende  
af rækker og kolonner, som overholder et bestemt sæt af karakteristika**

De karakteristika, som en tabel skal opfylde for at betegnes en relation, er angivet i [[Table|tabellen]] forneden:

| Regel | Beskrivelse af karakteristika                                                                                 |
| ----- | ------------------------------------------------------------------------------------------------------------- |
| 1     | Hver række i tabellen indeholder [[Data\|data]] (helt eller delvist) om en bestemt [[Entity\|entitet]]        |
| 2     | Hver kolonne i tabellen indeholder [[Data\|data]] om en bestemt attribut (egenskab) ved [[Entity\|entiteten]] |
| 3     | En celle i en [[Table\|tabel]] må kun indeholde en enkelt værdi                                               |
| 4     | Alle værdier i celler under en bestemt kolonne skal være af samme [[SQL Data Types\|type]]                    |
| 5     | Hver kolonne skal have et unikt navn                                                                          |
| 6     | Rækkefølgen af kolonner har ingen betydning                                                                   |
| 7     | Rækkefølgen af rækker har ingen betydning                                                                     |
| 8     | To rækker må ikke have identiske sæt af værdier i dets celler                                                 |

---

### Karakteristika 1: Hvad dækker præcist en entitet? 
Da der kan være mange rækker i en tabel, da beskriver hver række således forskellige instanser af én bestemt [[Entity|entitet]]. En [[Entity|entitet]] er dermed ikke et objekt, men en beskrivelse af fællestræk for et antal instanser (svarende til en klasse).

 Der kan dog opstå et problem, hvis en [[Table|tabel]] af en eller grund derimod beskriver flere entiteter på en gang. Hvis man forestiller sig en [[Table|tabel]] med følgende tre kolonner:

- SemesterNr
- FagTitel
- DeltagerNavn

[[Table|Tabellen]] dækker over tre entiteter, nemlig Semester, Fag og Deltager, og opfylder dermed ikke  karakteristika 1. 

En sådan [[Table|tabel]] vil ikke være en [[Relationer|relation]] og skal typisk opdeles, så hver ny [[Table|tabel]] kun beskriver en [[Entity|entitet]] hver.

---

### Karakteristika 2: Hvad er en attribut/egenskab for en entitet? 
En kolonne i en [[Table|tabel]] beskriver en attribut for en [[Entity|entitet]]. 
Dette svarer tilsvarende i den objekt-orienterede tilgang til, at en attribut i en konceptuel klasse i en [[Repo/01 - Systemudvikling og virksomhed/Artefakter/Domænemodel|Domænemodel]] beskriver en enkelt egenskab for klassen. 

Og på samme måde som hvert objekt dannet fra en klasse vil have en værdi for attributten, vil hver række i [[Table|tabellen]] have en relevant værdi for den specifikke kolonne.

For en [[Table|tabel]], der beskriver en person, vil dette kunne illustreres med:

|   |   |   |
|---|---|---|
||Name|Age|
|1|John Carter|35|
|2|Charles Darwin|213|

hvor de to kolonner Name og Age netop beskriver to forskellige egenskaber ved en person.

---

### Karakteristika 3: Én værdi i en celle 
Denne regel angiver, at der kun må være én værdi i hver celle. Dette er ikke tilfældet i [[Table|tabellen]] forneden:

|   |   |   |
|---|---|---|
||Name|Age|
|1|John Carter (single)|35|
|2|Charles Darwin (married)|213|

som så ikke kan betegnes en relation.


Ændres [[Table|tabellen]] derimod til:

|   |   |   |   |
|---|---|---|---|
||Name|Age|MaritalStatus|
|1|John Carter|35|single|
|2|Charles Darwin|213|married|


Nu er [[Table|tabellen]] en [[Relationer|relation]] set ud fra dette karakteristika, hvor hver celle nu kun har én værdi.

---

### Karakteristika 4: Alle værdier i celler under en bestemt kolonne skal vare af samme type 
Værdierne i en kolonne skal være af samme type/slags. F.eks. tabellen:

|     |                |         |
| --- | -------------- | ------- |
|     | Name           | Age     |
| 1   | John Carter    | 35      |
| 2   | Charles Darwin | 213     |
| 3   | 63             | Married |
| 4   | IT konsulent   | 42      |
Række 3 kolonne 3 har en string i stedet for en int.

---

### Karakteristika 5: Hver kolonne skal have et unikt navn 
Navnet på en kolonne skal være unikt, så nedenstående går ikke:

|   |   |   |   |
|---|---|---|---|
||Name|Age|Name|
|1|John Carter|35|Developer|
|2|Charles Darwin|213|HR konulent|

Her er løsningen at ændre det tredje kolonnenavn til f.eks. ’Profession’:

|     |             |
| --- | ----------- |
| Age | Profession  |
| 35  | Developer   |
| 213 | HR konulent |

---

### Karakteristika 6 og 7: Rækkefølgen pa kolonner og rækker 
Disse to regler angiver ganske simpelt, at rækkefølgen af rækker i tabellen overhovedet ingen betydning må have. 
Det samme gælder for kolonner. Dvs. man må i en [[Relationer|relation]] ikke forvente en bestemt rækkefølge.

---

### Karakteristika 8: To rækker ma ikke have identiske sæt af værdier i dets celler

|   |   |
|---|---|
|Name|Age|
|1|James Smith|25|
|2|James Smith|25|

  

Hvis det faktisk repræsenterer to forskellige personer tilfældigvis med samme navn og alder, så skal man introducere en ekstra kolonne, som gør hver række unik, dvs. det der kaldes en [[PRIMARY KEY|primærnøgle]].

  

Et eksempel kunne være at introducere en PersonId-kolonne med unikke værdier:

|   |   |   |   |
|---|---|---|---|
||PersonId|Name|Age|
|1|1|James Smith|25|
|2|2|James Smith|25|