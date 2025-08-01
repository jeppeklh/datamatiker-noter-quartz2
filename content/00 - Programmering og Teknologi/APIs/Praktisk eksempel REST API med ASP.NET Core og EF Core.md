
## Context klasse for databasen
---

Vi laver en context klasse som bruges til at kommunikere med Entity Framework. Den beskriver hvordan databasen hænger sammen og relationerne mellem tabellerne/entities.
Vi kalder den i dette eksempel ``ShopContext``. Fordi den repræsenterer vores webshop.
```csharp
// Implenterer DBContext 
public class ShopContext : DbContext 
{
	public ShopContext(DbContextOptions<ShopContext> options) : base(options) 
	{
		
	}
	// Bliver kørt når modellen kører. Den opstiller kardinalitet/multiplicitet mellem tabellerne. Her har en kategori mange produkter og et produkt har 1 kategori
	protected override void OnModelCreating(ModelBuilder modelBuilder)
	{
		modelBuilder.Entity<Category>()
			.HasMany(c => c.Products)
			.WithOne(c => c.Category)
			.HasForeignKey(c => c.CategoryId);
		// Her er Seed en extension metode vi selv har lavet på ModelBuilder klassen. Den populerer databsed med noget dummy data.
		modelBuilder.Seed();
	}
	// Vi opsætter vores DbSets som er tabeller i databasen
	public DbSet<Product> Products { get; set; }
	public DbSet<Category> Categories { get; set; }

	}
```

Vi skal nu fortælle applikationen at vi bruger denne Contextklasse. Det gør vi i ``Program.cs`` ved at tilføje dette:
```csharp
	builder.Services.AddDbContext<ShopContext>(options =>
	{
		options.UseInMemoryDatabase("Shop");
	});
```
Den foræller at vi bruger ShopContext og specificerer at vi bruger vores InMemoryDatabase som vi har lavet via Entity Framework.

## Retriving Data
---

### Returner en liste af items (GetAll)
---
Nu kan vi så bruge vores context klasse i vores Controller klasse:
```csharp
	[Route("api/[controller]")]
	[ApiController]	
	public class ProductsController : ControllerBase
	{
		private readonly ShopContext _context;

		// Dependency injection af vores context klasse
		public ProductsController(ShopContext context)
		{
			_context = context;

			// Ensures seeding (dummy data)
			_context.Database.EnsureCreated();
		}

		[HttpGet]
		public IEnumerable<Product> GetAllProducts()
		{
			return _context.Products.ToList();
		}
```

Således har vi nu lavet et [[API]]-endpoint, som returnerer alle produkter.

En anden måde at returnere nået fra vires API er ved at bryge et ActionResult. Dette sender statuskoder med, somer bedst practice. 

```csharp
[HttpGet]
public ActionResult<IEnumerable<Product>> GetAllProducts()
{
	var products = _context.Products.ToList();
	return Ok(products);
}
```

### Returning af et enkelt item
---
Vi definerer først [[API#Routing|routen]] til det specifikke item.
```csharp
// Vi definerer routen til det specifikke item [HttpGet][Route("api/products/{id}")]
// Eller vi kunne bare bruge id fordi vi har specificeret base routen i selve denne controller klasse [Route("api/[controller]")]
// [HttpGet][Route("{id}")]

// Eller endnu kortere
[HttpGet("{id}")]
public ActionResult<Product> GetProduct(int id) 
{
	var product = _context.Products.Find(id);
	return Ok(product);
}
```
Nu kan vi det api input i Swagger når vi kører applikationen:
![[SwaggerAPIEndpointVisual.png]]

### Error handling
---
Hvis vi prøver at returnere et item med et id der ikke findes i database, får vi en Undocumentet fejl kode 204. 
![[SwaggerUndocumentedStatusCodeExample.png]]
Denne kode betyder 'No Content'. Hvilket giver mening i vores eksempel. Vi kan dog håndtere dette i vores kode.
```csharp
[HttpGet("{id}")]
public ActionResult<Product> GetProduct(int id) 
{
	var product = _context.Products.Find(id);
	if (product == null)
	{
		return NotFound();
	}
	return Ok(product);
}
```

Her returnerer vores GetProduct metode NotFound(), hvis produktet ikke findes. Dette giver en 404 statuskode.

### Gøre API Asynkron
---
Vi gør vores HTTP kald asynkron ved at ændre metode signaturen til at være `async` og returtypen om til `Task<ActionResult>`. Vi skal også bruge `await`- keywordet når vi kalder asynkront. Dette kan give performancefordele ved større 'loads'.
```csharp
[HttpGet]
public async Task<ActionResult> GetAllProducts()
{
	var products = await _context.Products.ToListAsync();
	return Ok(products);
}

[HttpGet("{id}")]
public async Task<ActionResult> GetProduct(int id)
{
	var product = await _context.Products.FindAsync(id);
	if (product == null)
	{
		return NotFound();
	}
	return Ok(product);
}
```

## Writing Data
---

### Model binding
---
Vores GetProduct [[Action method]] forventede en parameter. I det tilfælde kom den parameter fra routen. Men argumenter kan også komme fra andre steder f.ek.s ander dele af HTTP-requesten
Der er 3 vigtige steder de kommer fra
`[FromBody]`
Dataen kommer fra 'the body'af en HTTP request. Altså hele kroppen af en HTTP-request (oftest POST/PUT) skal skal bruges og bindes til action metoden.

`[FromRoute]`
Dataen kommer fra en route template. Vi brugte ikke FromRoute i ovenstående eksempel, fordi vores web API var klog nok til at gøre det for os `bag scenen`. Men det er bedst at gøre det explicit, for hvad sker der hvis der er et ID i både routen og i HTTP-requesten.

`[FromQuery]`
Dataen kommer fra URLen en query string. 
### Tilføjelse af item med POST
---
Når vi laver ny data, bruger vi  [[REST API#**HTTP-metoder**|HTTP-metoden]] `POST`. 

Returtypen er her `Product`- vores selvlavede klasse. ASP.NET CORE's web API laver selv et `Product`-objekt ud fra de værdier som bliver sent som en del af HTTP-requesten. 

Når vi tilføjer et nyt item bruger vi metoden `CreatedAtAction`. Den tager 3 parametre:
- Navnet på den metode der er ansvarlig for at hente et enkelt item - i vores tilfælde `GetProduct`
- Et id. Men id'et er typisk en del af routen. Så vi angiver et annonymt object, hvor vi sætter Id'et til id'et af de product som vi lige tilføjede til databsem.
- Selve produktet

``` csharp
[HttpPost]
public async Task<ActionResult> PostProduct(Product product)
{
	_context.Products.Add(product);
	await _context.SaveChangesAsync();
	return CreatedAtAction(
		"GetProduct",
		new { id = product.Id },
		product);
}
```

### Model validation
---
Vi kan tilføje `[Required]` til bestemte model properties. Dete betyder at disse properties SKAL angives for at kunne tilføje et item.  Her tilføjer vi `[Required]` til Product's CategoryID
```csharp
[Required]
public int CategoryId { get; set; }
```
Hvis CategoryId nu ikke bliver angivet når vi forsøger at oprette et Product, får vi en status kode 400: Bad Request. Dette er defaulten. Vi kan supresse denne status kode i `Program.cs`-klassen ved at ændre
```csharp
builder.Services.AddControllers();
```
til
```csharp
builder.Services.AddControllers()
	.ConfigureApiBehaviorOptions(options =>
	{
		options.SuppressModelStateInvalidFilter = true;
	});
```

Derefter ville vi kunne lave vores egen logik, hvis en modelstate var invalid - Altså hvis required properties ikke er angivet:
```csharp
[HttpPost]
public async Task<ActionResult> PostProduct(Product product)
{
	// Hvis en required property ikke er angivet er modelstate invalid
	if (!ModelState.IsValid)
	{
		// Custom errorhandling here
	}


	_context.Products.Add(product);
	await _context.SaveChangesAsync();
	return CreatedAtAction(
		"GetProduct",
		new { id = product.Id },
		product);
}
```

### Updating an item with PUT
---
Vores Put metode tager 2 argumenter. 
- Id - hvilket item vi sjal opdatere
- `[FromBody]` Product product - det faktiske produkt, altså det opdaterede data. Vi forventer at det kommer fra kroppen af en HTTP-request, deraf FromBody.
Derefter sætter vi den ændrede entry's state til modified, så næste gang vi kalder SaveChanges eller persisterer data, bliver den opdateret.
Vi gemmer ændringerne og returnerer ingen ting.

Vi laver desuden lidt error handling. F.eks. hvis der opstår et concurrenct issue - alstå måske er produktet allerede blevet modificeret gennem et andet API kald. Eller hvis det er blevet slettet.

```csharp
[HttpPut("{id}")]
public async Task<ActionResult> PutProduct(int id, Product product)
{
	// Har produktet det samme Id som id'et i URI'en
	if (id != product.Id)
	{
		return BadRequest();
	}

	// Vi sætter det opdaterede produkts state til modified
	_context.Entry(product).State = EntityState.Modified;
	// Gemmer ændringerne
	try
	{
		await _context.SaveChangesAsync();
	}

	catch (DbUpdateConcurrencyException)
	{
		// Smid notfound hvis den ikke findes (altså er blevet slettet af et anden API kald)
		if (!_context.Products.Any(p => p.Id == id)) 
		{
			return NotFound();
		}
		// Ellers smid en default fejl.
		else
		{
			throw;
		}
	}
	// returner ingenting
	return NoContent();
}
```

### Sletning af item med DELETE
---
Vi bruger DELETE HTTP-metoden. Vi angiver id'et i routen og bruger id som en parameter. Vi tjekker om der findes et item med dette id - hvis ikke returneres statuskoden notfound.  Så fjerner vi itemmet fra databasen og gemmer.

Ved de fleste APIs returnerer man det item man lige har slettet.
```csharp
[HttpDelete("{id}")]
public async Task<ActionResult<Product>> DeleteProduct(int id)
{
	var product = await _context.Products.FindAsync(id);

	if (product == null) return NotFound();

	_context.Products.Remove(product);
	await _context.SaveChangesAsync();
	
	return product;
}
```

## Sletning af flere produkter
---
Vi bruger HttpPost her fordi vi vil slette flere men ikke alle???
Vi bruger også en specifik route  til dette. Ikke HttpDelete men routen Delete.
Vi kan så iterere over alle vores ID'er i vores array og slette dem én for én. Men hvad sker der hvis en af de ID'er ikke findes? Så vil vi typisk heller ikke have de andre slettet. Altså vi vil have returneret en `NotFound` kode, hvis det sker.
Vi returnerer nu en liste af alle de slettede produkter.

```csharp
[HttpPost("{id}")]
[Route("Delete")]
public async Task<ActionResult> DeleteMultiple([FromQuery] int[] ids)
{
	var products = new List<Product>();

	foreach (var id in ids)
	{
		var product = await _context.Products.FindAsync(id);

		if (product == null)
		{
			return NotFound();
		}
		products.Add(product);
	}

	_context.Products.RemoveRange(products);
	await _context.SaveChangesAsync();

	return Ok(products);
}
```

## Resourcer
---
- [API Consumer/Producer Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_37/scormcontent/index.html#/lessons/dXernJESphMLlxbBN2T7mqqRqAiJgm31)