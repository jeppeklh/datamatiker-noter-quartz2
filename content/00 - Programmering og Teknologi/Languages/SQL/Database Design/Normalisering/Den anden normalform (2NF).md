---
aliases:
  - 2NF
---
tags: #Programmering #SQL

## Definition 
---
For at en tabel skal være i den anden normale form, skal den følge følgende 2 regler:

1. Tabellen skal være i [[Den første normalform (1NF)|1NF]]. 
    
2. Der bør ikke være nogen delvis afhængighed. (alle ikke-nøgleattributter er fuldt funktionelt afhængige af hele primærnøglen)
## Example
---
Dette eksempel bygger videre på [[Den første normalform (1NF)#Example|eksemplet]] i [[Den første normalform (1NF)|1NF]]

![[Den anden normalform eksempel 1.png]]
Tabellerne opfylder alle regler i 1NF, da der står [[Den første normalform (1NF)#Atomære værdier|atomære værdier]] i alle celler, kolonner navne er unikke, dataene i hver kolonne er på samme datatype.

### Fjern delvise afhængigeder
---
Student_ID og Course tilsammen udgør [[PRIMARY KEY|primærnøglen]], da hver især kan ikke alene bestemme alle attributter i relationen.  
  
Name, College og Rank er kun afhængige af Student_ID og ikke af Course. Teacher er kun afhængig af Course og ikke af Student_ID. Så har vi en [[Funktionel afhængigheder#Delvis funktionel afhængighed|delvis afhængighed]], der bryder 2NF.

For at fjerne [[Funktionel afhængigheder#Delvis funktionel afhængighed|delvise afhængigheder]] skal vi opdele tabellen, så hver tabel indeholder attributter, der er [[Funktionel afhængigheder#Fuld funktionel afhængihed|fuldt funktionelt afhængige]] af hele primærnøglen og forbinde dem gennem [[FOREIGN KEY|fremmednøglen]].


![[Den anden normalform eksempel 2.png]]
Alle ikke-nøgleattributter, der kan bestemmes af Student_ID er sat sammen i en tabel. Det samme er gjort ved Course.  

Relationen mellem Student og Course tabellerne bliver [[Relationsskema#M M|mange til mange (M:M)]] relation, da en studerende kan tilmelde flere fag og flere studerende tilmelder et fag. 
Derfor har vi brug for en link-tabel (Enrollment) til at repræsentere denne sammenhæng.

## Related Topics
---
- Link
- 

## Resources
---
- Link
- 