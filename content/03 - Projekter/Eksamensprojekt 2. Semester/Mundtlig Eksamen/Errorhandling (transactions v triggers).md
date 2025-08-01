
## Hvad der skal siges til hvert slide: 
---
### **Slide 1: Titel**
- Jeg vil snakke om hvordan vi har implementeret vores eget fejlhåndteringssystem i applikation. 

- Jeg starter med at forklare, hvorfor vi valgte transactions i C#  
	- hvordan det giver os fleksibilitet  
	- understøtter vores fejlhåndterings-system. 

- Så ser vi på, hvordan systemet fungerer i praksis
- Vi tager et kig på Flowet
	- Fra en fejl opstår i databasen, 
	- til den bliver præsenteret i applikationen. 
	
- Til sidst skal vi se på et konkret eksempel

### **Slide 2: Hvorfor Transactions i C#**
- Vi valgte at bruge transactions i C#, fordi det gav os muligheden for at samle logik og fejlhåndtering i applikationen i stedet for i databasen. 
- Gjorde det muligt for os at implementere det her fejlhåndterings system, 
	- Som giver os kontrol over hvordan fejl logges og præsenteres
- Det vil jeg dykke lidt nærmere ned i nu

### **Slide 3: Flowchart**
Lad os tage kig på flowet af vores fejlhåndtering
- Vi antager at der sker en fejl i databasen
- Den fejl bliver logget i databasen
- Vi henter den fejl fra databasen ind i applikationen med de nødvendige informationer
- Hvor vi smider en exception
- Til slut - Viser vi en Besked med de informationer

### **Slide 4: SQL Error Logging via Stored Procedures**
Lad os kigge på hvordan fejl bliver logget
- Fejllogningen sker på **database-niveau**, og det er bygget helt fra bunden af os.
- Vi har lavet vores egne **custom tabeller** og tilhørende stored procedures.

- Alle fejl logges i tabellen `ERROR_LOG`, der indeholder detaljer som fejlkode, besked, og hvilken stored procedure det er gået galt i.

- `ERROR_CATALOGUE` indeholder nogle faste fejlkoder og tilhørende fejlbeskeder
- bruges til at sikre, de er konsistente på tværs af applikationen
### **Slide 5: Logikken bag logning af fejl**
Logikken bag logning foregår i LogAndThrowError
- Stored proceduren
- Den logger detaljer om fejl i `ERROR_LOG`, som kan bruges til debugging senere. 
- Den kaster fejlen videre til den kaldene stored procedure som så sender den videre til applikationen, så den kan håndteres korrekt i C#.
- Hvis der skulle opstå fejl i selve logningsprocessen, håndterer den også det 
### **Slide 6: Hvordan håndteres fejl i applikationen?**
Nu er fejlen blevet smidt videre til applikationen så lad os kigge på hvordan den håndteres der.
Fejl bliver håndteret i vores ErrorHandler-klasse
-  via `Catch`-metoden som står for at vise fejlbeskeder til brugeren. 
- Hvis fejlen kommer fra databasen - altså er det en SQLException - hentes detaljer fra den sidst loggede fejl `ERROR_LOG` ved hjælp af `GetLastLoggedErrorMessage`. 

Dette gøres med metoden GetLastLoggedError
- Metoden kigger på om den sidst loggede fejl den har hentet er sket inden for 5 sekunder
- Hvis den er returnerer den en besked, der beskriver problemet.
- Mere Tekniske detaljer for at kunne lave debugging
### **Slide 7: Fejlhåndtering i praksis**
Her er et eksempel på, hvordan det fungerer i praksis. 
- Hvis der opstår en fejl ved sletning af en medarbejder, logges fejlen automatisk i `ERROR_LOG`. 
- Vi kan se under error_message
- Der er på en eller anden vis blevet forsøgt sletning på en Employee som ikke eksisterer i databasen
- og vi også hvilken stored procedure fejlen er sket i. . DeleteEmployee
- Fejlen bliver smidt videre til applikationen.
- Applikationen viser en besked i med de relevante detaljer fra den sidst loggede fejl. 

Formålet med det her system er at opdage og håndtere fejl på en smart måde
- Så vi nemt kan finde frem til, hvad der gik galt, hvor det gik galt, og forbedre applikationen løbende. 
- Det har på en måde været lidt en stedfortræder for unittesting. 
- Og virkelig gjort en forskel for, hvordan vi sikrer, at tingene kører stabilt.