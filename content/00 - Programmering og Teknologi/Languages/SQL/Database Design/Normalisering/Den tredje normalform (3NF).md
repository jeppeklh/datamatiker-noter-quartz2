---
aliases:
  - 3NF
---
tags: #Programmering #SQL

> [!tldr] Definition
> For at en tabel skal være i den trejde normale form, skal den følge følgende 2 regler:
>
> 1. Tabellen skal være i [[Den anden normalform (2NF)|2NF]]. 
>    
> 2. Denne bør ikke have transitiv afhængighed. (ingen ikke-nøgleattribut er transitiv afhængig af primærnøglen

---

## Example
Vi bygger videre på [[Den anden normalform (2NF)#Example|eksemplet]] i [[Den anden normalform (2NF)|2NF]].
![[Den tredje normalform eksempel 1.png]]

---

### Fjernelse af transitive afhængigheder
I Student tabel Student_ID er nu [[PRIMARY KEY|primærnøglen]].

[[Funktionel afhængigheder|Funktionelle afhængigheder]] i [[Table|tabellen]] er:  
**Student_ID** → Name  
**Student_ID** → College
**Student_ID** → Rank  
**College** → Rank

College og Rank er ikke-nøgleattributter og en (Rank) er funktionelt afhængig af en anden (College), der bryder 3NF, fordi den er en [[Funktionel afhængigheder#Transitiv funktionel afhængighed|transitiv afhængighed]].

For at fjerne transitive afhængigheder skal vi opdele tabellen, så hver tabel indeholder attributter, der er [[Funktionel afhængigheder#Fuld funktionel afhængihed|direkte funktionelt afhængige]] af [[PRIMARY KEY|primærnøglen]].

![[Den tredje normalform eksempel 2.png]]
Alle ikke-nøgleattributter, der kan bestemmes af Student_ID er sat sammen i Student tabel. 

Det samme er gjort ved College. Der blev også skabt en [[Relationsskema#1 M|en-til-mange (1:M)]] relation mellem Student og College tabeller.

---

## Related Topics
- Link
- 

---

## Resources
- Link
- 