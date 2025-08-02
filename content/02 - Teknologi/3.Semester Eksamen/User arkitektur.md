### Overordnet struktur
I vores projekt har vi en brugerstruktur, der tager udgangspunkt i ASP.NET Core Identity. Vi har valgt at adskille den tekniske identitetsstyring (login, roller, claims m.m.) fra de mere domænespecifikke brugeroplysninger (såsom ansat- eller kundeinformation). Strukturen ser således ud:

- **IdentityUser**: Denne klasse kommer fra `Microsoft.AspNetCore.Identity` og indeholder loginrelaterede felter som `UserName`, `Email`, `PasswordHash`, m.m.
    
- **ApplicationUser**: Arver fra `IdentityUser` og udvider med felter som `FirstName`, `LastName` og en `RowVersion` til concurrency control.
    
- **BaseUser** (abstrakt): Indeholder alle fælles forretningsdata (f.eks. `CustomUserName`, `ApplicationUser` navigation, og `RowVersion`).
    
- **Employee** og **Customer**: Arver begge fra `BaseUser`. De giver mulighed for at håndtere forskellige brugertyper med udgangspunkt i samme kernefunktionalitet.
    


Vi valgte at lave en `BaseUser`, som både `Customer` og `Employee` arver fra, for at samle alle fælles domænefelter ét sted. 
Det giver os mulighed for at udvide hver type senere, uden at skulle ændre i den fælles kerne. `Customer` er i øjeblikket tom, men vi har valgt at beholde den for at understøtte skalérbarhed og undgå unødigt omskrivningsarbejde. 
Desuden kan man sige, at vi dermed også har en klar semantisk skelnen mellem ansatte og kunder i vores model.

---

### Begrundelse for ikke at nedarve direkte fra IdentityUser
Vi valgte **ikke** at lade vores domænemodeller (som `Customer` eller `Employee`) arve direkte fra `IdentityUser`, fordi Visual Studio's **Entity Framework scaffolding-værktøj ikke fungerer optimalt** med klasser, der nedarver fra `IdentityUser`. 
Der opstår typisk problemer, når man forsøger at generere views og controllere til sådanne klasser. 
Det gør vedligeholdelse og udvikling mere besværlig.

Ved at introducere `ApplicationUser` og så holde `Customer` og `Employee` adskilt, sikrer vi en **ren separation mellem identitet og forretningslogik**, samtidig med at vi kan bruge scaffolding og EF Core som forventet.

---

### Hvorfor er `Customer`-klassen tom?
`Customer` er tom, fordi vi **oprindeligt havde en egenskab (`CustomUserName`)** som var unik for kunder, men valgte senere at flytte den til `BaseUser`, da vi også fik brug for den i `Employee`. Vi har valgt **at bevare `Customer`-klassen**, selvom den pt. ikke tilføjer nye felter. Det gør vi af følgende grunde:

1. **Skalerbarhed**: Hvis vi i fremtiden ønsker at tilføje felter eller logik kun for `Customer`, er strukturen allerede klar.
    
2. **Opgavefordeling og domæneadskillelse**: Det er tydeligt for andre udviklere (og i datamodellen), at `Customer` og `Employee` er to forskellige roller.
    
3. **Vedligeholdelsesbesparelse**: Hvis vi slettede `Customer`-klassen, skulle vi refaktorere hele koden, hvor den bliver brugt — f.eks. i services, views, databasen, og ved fremtidige migrationer. Det ville være omfattende og risikofyldt.
    
---

### Fordele ved denne arkitektur
---
- **Fleksibilitet**: Let at udvide med nye roller (f.eks. Partner, Agent osv.) ved at oprette nye klasser, der nedarver fra `BaseUser`.
    
- **Testbarhed**: Gør det lettere at teste forretningslogik, uden at Identity-komponenterne er i vejen.
    
- **EF Core-kompatibilitet**: Vi undgår problemer med scaffolding og databasegenerering.
    
- **Ren arkitektur**: Separation of concerns — identity og business holdes adskilt.
    






### Hvorfor ligger `FirstName` og `LastName` i `ApplicationUser` og ikke i `BaseUser`?
---
"Vi har valgt at placere `FirstName` og `LastName` i `ApplicationUser`, fordi det er oplysninger, der typisk bruges i forbindelse med login, profil og generel brugerhåndtering. Hvis de lå i `BaseUser`, ville vi skulle lave ekstra opslag i databasen for at vise brugerens navn, f.eks. i headeren. Ved at lade dem blive i `ApplicationUser`, understøtter vi en mere effektiv integration med ASP.NET Identity."