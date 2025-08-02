---
aliases:
  - Application Programming Interface
---

> [!tldr] Definition
> Et sæt regler og protokoller, der gør det muligt for forskellige softwarekomponenter at kommunikere med hinanden. API'er bruges til at udstille data og funktionalitet, så andre systemer eller klienter kan interagere med din applikation.

Der findes flere typer af API'er. En af dem er [[REST API]]

2 Approaches til API.
- Lav eget api (consumer) - [[Praktisk eksempel REST API med ASP.NET Core og EF Core|Eksempel]]
- Direkte API kald - [[Uge9 - API opgaver|API opgaver]]

Controllers håndterer HTTP requests og sørger for at det korekkete data bliver returneret.
Den controller klasse bliver så dekoreret med API-controller-attributten. Dette tilføjer nogle vigtige features. f.eks at data bliver serialiseret. 

I controlleren vil vi have nogle metoder - HTTP metoder. f.eks. en ``Get()`` C# metode, som er ansvarlig for GET-requests, indikeret ved `[HttpGet]`. Disse moetoder som håndterer HTTP requirests hedder Action methods.
```csharp
[HttpGet]
public Get() {

}
```

---

## Routing
mekanismen, der kortlægger indkommende HTTP-forespørgsler til de korrekte metoder ([[Action method]]s) i dine controllers. Ved at definere ruter kan du strukturere dine URL'er, så de afspejler de ressourcer, din applikation tilbyder.

| Attribute                    | Description                                                                                                                                                       |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `[Route("/products")]`       | Angiver, at forespørgsler til `/products` vil blive håndteret af den tilknyttede controller eller action method.                                                  |
| `[Route("/products/{id}")]`  | Her bliver `id` hentet direkte fra URL'en og kan bruges i din metode, fx til at hente et specifikt produkt.)                                                      |
| `[Route("/products/{id?}")]` | Den markerede parameter er nu valgfri.                                                                                                                            |
| `[Route("/[controller]")]`   | Denne konvention bruger controllerens navn (uden "Controller"-delen) som en del af URL'en. Hvis controlleren hedder ProductsController, bliver routen `/Products` |
Her bliver `[Route("/[controller]")]` brugt i Visual Studios template for API controllers. Det betuder at routen til denne controller er klassens navn minus "controller". Altså `api/Products`
![[APIRoutingEksempel.png]]
Hvis vi ville route til et bestemt id i en `GetAllProducts`-metode, kunne vi gøre således fordi vi allerede har en base route
```csharp
[HttpGet][Route("{id}")]
public async Task<ActionResult> GetProduct(int id)
{
	var product = await _context.Products.FindAsync(id);
	if (product == null)
	{
		return NotFound();
	}
	return Ok(product);
```
Eller endnu simplere:
```csharp
[HttpGet("{id}")]
```

---

## Serialisering
Serialisering er processen, hvorved objekter konverteres til et format, der kan sendes over et netværk – typisk JSON i web-API'er. Det sikrer, at data, der udstilles af API'et, bliver korrekt formateret og kan fortolkes af klientapplikationer.

#### Vigtige punkter ved serialisering:
- **Automatisk konvertering:**  
    Når du bruger attributten `[ApiController]`, håndterer ASP.NET Core automatisk serialisering af dine data.
- **Håndtering af cirkulære referencer:**  
    Ved komplekse objekter kan du bruge attributter som `JsonIgnore` for at undgå uendelige loops mellem sammenkoblede modelklasser.

---

## Eksempel på en simpel controller
```csharp
[ApiController]
[Route("api/[controller]")]
public class ProductsController : ControllerBase
{

    // Denne action method håndterer GET-forespørgsler og returnerer en liste af produkter
	[HttpGet]
	public async Task<ActionResult> GetAllProducts()
	{
		//hent produkter fra databasen of kom dem i en liste
		var products = await _context.Products.ToListAsync(); 
		return Ok(products); // Dataen bliver serialiseret til JSON
	}
}
```
---

## API Testing og debugging
##### Postman
Et værktøj til at teste API endpoints. Giver mulighed for at lave requests, tilføje headers, og se reponses struktureret.
##### Browser Dev Tools
Indbyggede værktøjer i browsers, hvor man kan se HTTP requrests og reposonses uden andet software.
##### Fiddler
Et proxy værktøj, der opfanger og analyserer HTTP trafik mellem browser og web-applikationen. Det giver insight og mulighed for at manipulerer requests.

---    

## Producer / Consumer
I forbindelse med WebAPI'er refererer "Producer" og "Consumer" til to forskellige roller eller enheder, der interagerer med API'et:

**Producer** 
Dette er den enhed, der leverer data eller tjenester via API'et. Producenten opretter og vedligeholder API'et, definerer de tilgængelige endpoints, og bestemmer, hvordan data skal struktureres og leveres. For eksempel kan en producent være en server, der tilbyder data om vejret, som andre applikationer kan tilgå.
	
**Consumer** 
Dette er den enhed, der bruger API'et til at hente data eller tjenester fra producenten. Forbrugeren sender anmodninger til API'et og modtager svar, som derefter kan bruges i applikationen. For eksempel kan en forbruger være en mobilapp, der viser vejrudsigter ved at hente data fra vejrtjenestens API.


Kort sagt, producenten leverer dataene, og forbrugeren bruger dataene.

---

## Resourser
- [API Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_35/scormcontent/index.html#/lessons/pXgGVCJuSbMjcThYav2SA69FMj2J0Lrh)
- [API LinkedIn](https://www.linkedin.com/learning/building-web-apis-with-asp-dot-net-core-in-dot-net)
- [[Praktisk eksempel REST API med ASP.NET Core og EF Core]]
- [API Consumer/Producer Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_37/scormcontent/index.html#/lessons/dXernJESphMLlxbBN2T7mqqRqAiJgm31)