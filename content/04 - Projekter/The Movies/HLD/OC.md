## Iteration 1
Baseret på [[Usecase#Use Case Tilføjelse af film|Usecase: Tilføjelse af film]]

|                                                                                               |
| --------------------------------------------------------------------------------------------- |
| Operation: TilføjFilm(titel: string, varighed: int, genre: string)                            |
| Cross Reference: Tilføj Film                                                                  |
| Preconditions:                                                                                |
| Postconditions: Et filmobjekt med titel, varighed og genre blev oprettet (instance creation). |

---

## Iteration 2
### Baseret på [[Usecase#Use Case 1 Tilføj Film|Usecase: Tilføjelse af film(opdateret)]]
|                                                                                                                             |
| --------------------------------------------------------------------------------------------------------------------------- |
| Operation: TilføjFilm(titel: string, varighed: int, genre: string, filminstruktør: string, premieredato: DateTime)          |
| Cross Reference: Tilføj Film                                                                                                |
| Preconditions:                                                                                                              |
| Postconditions: Et filmobjekt med titel, varighed, genre, filminstruktør og premieredato blev oprettet (instance creation). |


### Baseret på [[Usecase#Use Case 2 Tilføje ny forestilling|Usecase: Tilføje ny forestilling]]

|                                                                                                      |
| ---------------------------------------------------------------------------------------------------- |
| Operation: TilføjForestilling(Sal: string, spilletid: DateTime, film: Movie)                         |
| Cross Reference: Tilføje ny forestilling                                                             |
| Preconditions: Film-objekt findes, biograf-objekt findes.                                            |
| Postconditions: Et forestillingsobjekt med sal, film og spilletid blev oprettet (instance creation). |
