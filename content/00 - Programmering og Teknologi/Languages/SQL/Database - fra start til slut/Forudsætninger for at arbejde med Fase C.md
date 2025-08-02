tags: #Programmering #SQL

## Adgang til en Database Server 
Dette kan være en lokal SQL Server instans, en fjernserver eller en cloud-baseret [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]].

Dine tabeller skal allerede være oprettet i denne database, baseret på den database-model, du tidligere har designet og implementeret i fase [[Database Design|A]] og [[Database Implementering|B]].

---

## Installering a NuGet-Pakker
For at kunne arbejde med databaser i .NET, skal du installere nogle nødvendige NuGet-pakker i dit Visual Studio projekt.

---

#### Microsoft.Data.SqlClient
##### Beskrivelse
Denne pakke indeholder SQL Client API'en, som er essentiel for at kunne kommunikere med SQL Server.  

##### Installation
I Visal Studio kan du installere den ved at højreklikke på dit projekt i Solution Explorer, vælge "Manage NuGet Packages", søge efter "Microsoft.Data.SqlClient", og derefter installere den seneste version.

Alternativt kan du installere den via NuGet Package Manager Console med følgende kommando:  
`Install-Package Microsoft.Data.SqlClient`

---

#### Microsoft.Extensions.Configuration.Json
##### Beskrivelse
For at kunne læse appsettings.json filen i din applikation, skal du installere Microsoft.Extensions.Configuration.Json NuGet-pakken.  
##### Installation
Gå til NuGet Package Manager og søg efter "Microsoft.Extensions.Configuration.Json", eller installer den via Package Manager Console:  
`Install-Package Microsoft.Extensions.Configuration.Json`

---

## Oprettelse af appsettings.json Filen
For at forbedre konfigurationen af din C#-applikation, især når du arbejder med .NET Core eller nyere .NET-versioner, anbefales det at bruge appsettings.json til at gemme dine applikationsindstillinger, herunder connection strings.

#### Opret appsettings.json Filen  
Højreklik på dit projekt i Solution Explorer.     
Vælg "Add", derefter "New Item".  
Vælg "JavaScript JSON Configuration File".  
Navngiv filen appsettings.json.
    
---

#### Tilføj Connection String  
Du skal være i stand til at oprette forbindelse til SQL Server-databasen ved hjælp af en [[Connection String|connection string]].  
Åbn appsettings.json filen, og tilføj følgende JSON-struktur for at angive din connection string:

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

---

## Opsætninger i C#-Projektet
For at læse konfigurationen fra appsettings.json, skal du tilføje følgende kode i din applikation, typisk i Program.cs eller Startup.cs filen:

```csharp
using Microsoft.Extensions.Configuration;
.....

IConfigurationRoot config = new ConfigurationBuilder().AddJsonFile("appsettings.json").Build();

string? ConnectionString = config.GetConnectionString("DefaultConnection");
```

For at kunne bruge de funktioner, som de installerede NuGet-pakker tilbyder, skal du tilføje følgende "using-direktiver" i den C#-klasse, hvor du vil benytte dem:

```csharp
using Microsoft.Extensions.Configuration; // Til indlæsning af konfigurationsindstillinger fra appsettings.json
using System.Data;
using System.Data.SqlClient; // Til at arbejde med SQL Server via ADO.NET
```

---

#### Ændre "Copy to Output Directory" indstilling for appsettings.json
For at sikre, at appsettings.json-filen bliver kopieret til outputmappen under bygningen af projektet, skal du ændre filens egenskaber i Visual Studio.

- Åbn Projektmappen i Visual Studio og find din appsettings.json-fil i Solution Explorer.

- Højreklik på appsettings.json-filen og vælg "Properties" fra kontekstmenuen.

- I egenskaberne, find "Copy to Output Directory" dropdown-menuen.

- Skift denne indstilling fra "Do not copy" til "Copy always" eller "Copy if newer", afhængigt af dine behov. "Copy always" sikrer, at filen kopieres hver gang du bygger projektet, mens "Copy if newer" kun kopierer filen, hvis den er blevet ændret siden sidste bygning.

- Gem dine ændringer og byg projektet. appsettings.json skal nu være tilgængelig i outputmappen, typisk bin/Debug/netcoreappX.Y/ eller en tilsvarende mappe, afhængigt af dit projekts opbygning.

---

## Related Topics
- Link
- 

---

## Resources
- [Database-tilgang Læringsobjekt (Forudsætninger)](https://rise.articulate.com/share/65tiUowEA12ttXX3SsFPiF1jJxG8gdCJ#/lessons/N2E_qWWZmH44zvElVtWMzlIJt6xkFK5y)
