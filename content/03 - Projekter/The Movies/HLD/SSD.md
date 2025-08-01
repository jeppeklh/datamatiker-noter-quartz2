	
## Iteration 1
---
Baseret på [[Usecase#Use Case Tilføjelse af film|Usecase: Tilføjelse af film]]

```plantuml
@startuml  
actor Medarbejder

Medarbejder -> System: TilføjFilm(titel, varighed, genre)  
System -> Medarbejder: "Film oprettet"

@enduml
```

## Iteration 2
---
### Baseret på [[Usecase#Use Case 1 Tilføj Film|Usecase: Tilføjelse af film (opdateret)]]
```plantuml 
@startuml  
actor Medarbejder

Medarbejder -> System: TilføjFilm(titel, varighed, genre, filminstruktør, premieredato)  
System -> Medarbejder: "Film oprettet"

@enduml
```

### Baseret på [[Usecase#Use Case 2 Tilføje ny forestilling|Usecase: TilFøje ny forestilling]]
```plantuml
@startuml

title Use Case 2: Tilføje ny forestilling  
actor Medarbejder as M

M -> System : TilføjForestilling(Biograf, Sal, Spilletid, Film)  
System --> M : Forestilling oprettet

@enduml
```
