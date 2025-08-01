tags: #Programmering #SQL

## Definition 
---
En [[string|streng]], der indeholder de nødvendige oplysninger for at kunne oprette forbindelse til en [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] (serveradresse, databasenavn, brugernavn og kodeord).

Det tilsvarende til filepath til csv-fil. Dette er bare til databasen.
## Syntax
---
##### Windows Authentication
Denne metode bruger de aktuelle Windows-brugeroplysninger til at få adgang til databasen.
```json
  "ConnectionStrings": {
    "DefaultConnection": "Server=YOUR_SERVER_NAME;Database=YOUR_DATABASE_NAME;Trusted_Connection=True;"
  }
```

##### SQL Server Authentication
Denne metode kræver et SQL Server-brugernavn og adgangskode for at få adgang til databasen.
```json
 "ConnectionStrings": {
    "DefaultConnection": "Server=YOUR_SERVER_NAME;Database=YOUR_DATABASE_NAME;User Id=YOUR_USERNAME;Password=YOUR_PASSWORD;"
  }
```

### Example
---





## Related Topics
---
- Link
- 

## Resources
---
- Link
- 