### Hvad er forskellen på unit test, integration test og UI test?
---
**Unit test** 
Tester en enkelt klasse eller metode isoleret, f.eks. validering af input. Ingen afhængigheder bruges direkte (mockes typisk).

**Integration test** 
Tester samspil mellem flere dele, f.eks. database og service sammen.

**UI test (f.eks. Bunit)** 
Tester hvordan brugergrænsefladen opfører sig, f.eks. navigation eller om en komponent viser korrekt data.


### Hvordan bruger du mocks og hvorfor?
---
Vi bruger **mocks** (f.eks. med Moq) til at **erstatte eksterne afhængigheder**, som fx databaser eller services.

Det sikrer, at testen kun fokuserer på **logikken i den ene komponent**, og ikke fejler pga. noget eksternt.
  

### Hvordan sikrer du at din kode er testbar?
---
Ved at bruge **interfaces** (f.eks. `IExtendedUserService`) og **dependency injection**.

Vi undgår "hardcoded" afhængigheder og **deler ansvar** op i små klasser.

Det gør det nemt at **isolere og teste** hver del uden at skulle køre hele applikationen.


### Hvordan håndterer du fejl i din app (null, exceptions, redirects)?
---
Vi tjekker fx for `null` i komponenter og **redirecter** til en fejl- eller "notfound"-side.

I services bruger vi `try-catch` eller lader en exception kastes og fanger den højere oppe.

Vi tester også fejlscenarier, som når data ikke findes.


### Hvordan validerer du data i inputmodeller?
---
Vi bruger **DataAnnotations** som `[Required]`, `[Range]` osv. i vores inputmodeller.

I tests kalder vi `Validator.TryValidateObject()` for at sikre, at valideringen fungerer korrekt.


### Hvorfor er det vigtigt at teste både success og failure scenarier?
---
Fordi kode skal fungere både **når alt går godt** og **når noget går galt**.
    
Success-tests bekræfter korrekt funktion.
 
Failure-tests sikrer, at appen **fejler på en kontrolleret måde** (f.eks. med en fejlbesked eller redirect).
  

### Hvordan bruger du `Bunit` til komponenttest?
---
`Bunit` gør det muligt at **rende Blazor-komponenter i testmiljøet**.

Vi bruger `RenderComponent<T>()` til at køre komponenten og tjekke f.eks.:

- Om der vises det rigtige.

- Om der sker navigation ved fejl.

- Om en knap klikker fungerer korrekt.


### Hvordan fungerer `TestInitialize` og `Setup` i MSTest?
---
`TestInitialize`-metoden køres **før hver enkelt test**.
 
Vi bruger den til at **initialisere mocks**, afhængigheder og testmiljø.

Det sikrer, at hver test starter med **en frisk og korrekt opsætning**.




### Hvorfor er det vigtigt at adskille dataadgang og præsentation i test?
---
Det gør det muligt at **teste præsentationslaget (UI)** uden at være afhængig af database/dataadgang.

Ved at **mocke data**, kan vi fokusere på hvordan UI reagerer, uanset hvordan data hentes.

Det skaber **robuste og hurtige tests** og gør koden **mere vedligeholdelig**.