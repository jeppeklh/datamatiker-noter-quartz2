---
aliases:
  - redundans
  - Redundancy
  - redundancy
---
tags: #Programmering #SQL

## Definition 
---
**Redundans** betyder at have flere kopier af de samme data i databasen. Dette problem opstår, når en database ikke er normaliseret.   

**Redundans** kan forårsage forskellige problemer såsom datainkonsistens, højere lagerkrav og langsommere datahentning.
## Example
---
Antag, at en tabel med attributter for studerendeoplysninger er: student ID, student name, college name, college rank, teacher and course.

|                |          |             |             |             |             |          |
| -------------- | -------- | ----------- | ----------- | ----------- | ----------- | -------- |
| **Student_ID** | **Name** | **Contact** | **College** | **Course**  | **Teacher** | **Rank** |
| 100            | Jens     | 73009348    | UCL         | Programming | Thomas      | 2        |
| 101            | Hans     | 79007348    | UCL         | Programming | Thomas      | 2        |
| 102            | Patrick  | 73009015    | UCL         | Programming | Thomas      | 2        |
| 103            | Pia      | 73009367    | UCL         | Programming | Thomas      | 2        |
Værdier for attributtens college name, college rank, course og Teacher gentages, hvilket kan føre til problemer. 
Hvis en tabel har dataredundans, så vil den ikke kun tage ekstra hukommelsesplads, men vil også gøre det vanskeligt for dig at håndtere og opdatere [[Data|dataene]] i [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|databasen]] uden at miste data.  
Problemer, der kan opstå på grund af redundans er:

- [[Anormali#Indsætningsanormalier|Indsætningsanormalier]]
- [[Anormali#Opdateringsanormalier|Opdateringsanormalier]]
- [[Anormali#Sletningsanormalier|Sletningsanormalier]]

## Header2
---



## Related Topics
---
- Link
- 

## Resources
---
- Link
- 