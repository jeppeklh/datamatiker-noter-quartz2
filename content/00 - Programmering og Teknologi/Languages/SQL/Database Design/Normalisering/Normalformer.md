tags: #Programmering #SQL

## Definition 
---
[[Normalisering]] processen fungerer gennem et sæt formelle kriterier og regler kaldes normalformer (Normal Forms).

Normalformerne gælder for individuelle relationer. Relationen siges at være i særlig normalform, hvis den opfylder nogle begrænsninger.
## Normalformtyper
---
[[Den første normalform (1NF)]]
[[Den anden normalform (2NF)]]
[[Den tredje normalform (3NF)]]
## Eksempel: fra unormaliseret til den tredje normalform
---
##### Unormaliseret
![[Unormaliseret (Normalform eksmpel).png]]

##### 1NF
---
I 1NF skal alle attributter have atomære værdier. Vi deler rækkerne op, så hver celle kun indeholder en enkelt værdi.
![[Den første normalform eksempel.png]]
##### 2NF
---
I 2NF skal tabellen være i 1NF, og vi skal fjerne [[Funktionel afhængigheder#Delvis funktionel afhængighed|delvise afhængigheder]]. 
En attribut er delvist afhængig, hvis den afhænger af en del af en sammensat nøgle. Vi skaber separate tabeller for Student og Course og bruger fremmednøgler til at forbinde dem.

![[Den anden normalform eksempel 2.png]]
##### 3NF
---
I 3NF skal tabellen være i 2NF, og vi skal fjerne transitive afhængigheder. En transitive afhængighed betyder, at en ikke-nøgle attribut afhænger af en anden ikke-nøgle attribut. 
Rank er afhængig af College, så vi skal oprette en separat College tabel.

![[Den tredje normalform eksempel 2.png]]


## Related Topics
---
- Link
- 

## Resources
---
- Link
- 