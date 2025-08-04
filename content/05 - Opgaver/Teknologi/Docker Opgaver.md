
# Opgave: Docker Image  med .NET
## Introduktion
I denne opgave skal I arbejde med at oprette, optimere og forstå Docker images med .NET. I vil lære om image "lagdeling", hvordan vi kan optimere og hvordan man skaber effektive, sikre containere.

## Tidsramme
Fra kl. 09:45 til 12:00

---

## Del 1: Byg et simpelt .NET Web API
### Opgave
Opret et simpelt REST API med .NET, og byg et Docker image til det.

### Trin (Sidder på en Mac, i kan bare lave ny solution i Visual Studio med en Web API)
1. Opret en ny mappe til projektet:
```bash
mkdir product-api
cd product-api
```

2. Opret et nyt .NET Web API projekt:
```bash
dotnet new webapi
```

3. Opret en ny model klasse `Product.cs` i en mappe kaldet `Models`:
```csharp
namespace ProductApi.Models
{
    public class Product
    {
        public int Id { get; set; }
        public string Name { get; set; }
        public decimal Price { get; set; }
    }
}
```

4. Opret en controller `ProductsController.cs` i `Controllers` mappen:
```csharp
using Microsoft.AspNetCore.Mvc;
using ProductApi.Models;
using System.Collections.Generic;
using System.Linq;

namespace ProductApi.Controllers
{
    [ApiController]
    [Route("api/[controller]")]
    public class ProductsController : ControllerBase
    {
        private static List<Product> _products = new List<Product>
        {
            new Product { Id = 1, Name = "Laptop", Price = 8999M },
            new Product { Id = 2, Name = "Smartphone", Price = 5499M },
            new Product { Id = 3, Name = "Headphones", Price = 1299M }
        };

        // GET: api/products
        [HttpGet]
        public ActionResult<IEnumerable<Product>> GetProducts()
        {
            return _products;
        }

        // GET: api/products/5
        [HttpGet("{id}")]
        public ActionResult<Product> GetProduct(int id)
        {
            var product = _products.FirstOrDefault(p => p.Id == id);
            
            if (product == null)
            {
                return NotFound();
            }
            
            return product;
        }

        // POST: api/products
        [HttpPost]
        public ActionResult<Product> CreateProduct(Product product)
        {
            if (product == null || string.IsNullOrEmpty(product.Name) || product.Price <= 0)
            {
                return BadRequest("Product needs a name and a valid price");
            }
            // Kan laves som en one-liner. Bare sværere at læse
            // int newId = _products.Count > 0 ? _products.Max(p => p.Id) + 1 : 1;
            
            // Find det næste ledige id
            int newId;
            if (_products.Count > 0) {
               // Hvis der findes produkter, tag det højeste id og læg 1 til
               newId = _products.Max(p => p.Id) + 1;
            } else {
               // Hvis listen er tom, start med id 1
               newId = 1;
            }
            
            product.Id = newId;
            
            _products.Add(product);
            
            return CreatedAtAction(nameof(GetProduct), new { id = product.Id }, product);
        }
    }
}
```
4. Installer 
   ```bash
   dotnet add package Swashbuckle.AspNetCore
   ```
5. Opdater Program.cs til at tilføje CORS:
```csharp
var builder = WebApplication.CreateBuilder(args);

// Add services to the container.
builder.Services.AddControllers();
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();
builder.Services.AddCors(options =>
{
    options.AddDefaultPolicy(
        policy =>
        {
            policy.AllowAnyOrigin()
                  .AllowAnyHeader()
                  .AllowAnyMethod();
        });
});

var app = builder.Build();

// Configure the HTTP request pipeline.
app.UseSwagger();
app.UseSwaggerUI();

app.UseHttpsRedirection();
app.UseCors();
app.UseAuthorization();
app.MapControllers();

app.Run();
```

1. Sørg for at appsettings.json har Kestrel(.nets webserver) konfigureret til følgende:
   (0.0.0.0 betyder alle tilgængelige netværksinterfaces)
```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "Kestrel": {
    "Endpoints": {
      "Http": {
        "Url": "http://0.0.0.0:80"
      }
    }
  }
}
```

1. Opret en `Dockerfile` med dette indhold:(Hedder 'Dockerfile' uden filendelse)
```Dockerfile
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src

# Kopier projektet og gendan afhængigheder
COPY *.csproj ./
RUN dotnet restore

# Kopier resten af filerne og byg projektet
COPY . .
RUN dotnet build -c Release -o /app/build

# Publicer projektet
FROM build AS publish
RUN dotnet publish -c Release -o /app/publish

# Opbyg runtime image
FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS final
WORKDIR /app
COPY --from=publish /app/publish .
EXPOSE 80
ENTRYPOINT ["dotnet", "product-api.dll"]
```

8. Byg dit image: (JA! Der skal være . til sidst!)
```bash
docker build -t product-api:v1 .
```

9. Kør containeren:
```bash
docker run -p 8080:80 product-api:v1
```

10. Test API'et:
    - Åbn en browser og gå til: http://localhost:8080/swagger/index.html

## Del 2: Analysér Docker Image Størrelse
---
### Opgave
Undersøg størrelsen og "lagene" i dit Docker image.

### Trin
1. Se størrelsen på dit image:
```bash
docker images product-api:v1
```

2. Undersøg "lagene" i dit image:
```bash
docker history product-api:v1
```

3. Analysér hvilke lag der fylder mest og hvorfor

4. Diskutér i gruppen:
   - Hvad er fordelene og ulemperne ved den nuværende image størrelse?
   - Hvilke dele af imaget kan potentielt reduceres?

---

## Del 3: Optimér Docker Image (45 minutter)

### Opgave
Opret et optimeret Docker image for din .NET applikation.

### Trin
1. Opret en ny `Dockerfile.optimized` med disse forbedringer: (Alpine er en ekstrem lille Linux destribution(5-10mb))
```Dockerfile
# Build stage
FROM mcr.microsoft.com/dotnet/sdk:9.0-alpine AS build
WORKDIR /src

# Kopier kun .csproj-filen først for bedre lag-caching
COPY *.csproj ./
RUN dotnet restore

# Kopier resten og byg
COPY . .
RUN dotnet build -c Release -o /app/build

# Publish stage
FROM build AS publish
RUN dotnet publish -c Release -o /app/publish /p:UseAppHost=false

# Final stage
FROM mcr.microsoft.com/dotnet/aspnet:9.0-alpine AS final
WORKDIR /app

# Opret en ikke-root bruger til at køre applikationen
# Brug --system flag i stedet for -S, som er tvetydigt
RUN addgroup --system appgroup && adduser --system --ingroup appgroup appuser

# Kopier kun de publicerede filer
COPY --from=publish /app/publish .

# Sæt ejerskab og rettigheder
RUN chown -R appuser:appgroup /app
USER appuser

EXPOSE 80

ENTRYPOINT ["dotnet", "product-api.dll"]
```

2. Byg det optimerede image:
```bash
docker build -t product-api:v2 -f Dockerfile.optimized .
```

3. Sammenlign størrelsen:
```bash
docker images | grep product-api
```

4. Kør det optimerede image:
```bash
docker run -p 8081:80 product-api:v2
```

5. Test at det virker: http://localhost:8081/swagger/index.html

---

## Del 4: Multi-stage Builds og Lagindsigt

### Diskussion i grupper
Diskutér følgende spørgsmål i jeres grupper:

1. Hvordan fungerer multi-stage builds i Docker?
2. Hvordan kan man yderligere reducere image-størrelsen?

---

## Ressourcer
- [.NET og Docker Best Practices](https://docs.microsoft.com/en-us/dotnet/architecture/microservices/net-core-net-framework-containers/official-net-docker-images)
- [Optimering af Docker Images](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [Docker Multi-stage Builds](https://docs.docker.com/build/building/multi-stage/)

---

# Opgave 2: Docker Compose med .NET

## Introduktion
I denne opgave skal I arbejde med Docker Compose til at opsætte og køre en multi-container applikation bestående af et .NET Web API og en SQL Server database.

---

## Del 1: Opret en .NET applikation med database
### Opgave
Opret et .NET Web API, der gemmer data i en SQL Server database, og konfigurer det hele med Docker Compose.

### Trin

1. Opret en ny mappe til projektet:
```bash
mkdir product-system
cd product-system
```

2. Opret et nyt .NET Web API projekt eller brug dit projekt fra formiddagen:
```bash
dotnet new webapi -n ProductApi
cd ProductApi
```

3. Tilføj Entity Framework Core pakker:
```bash
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Design
```

4. Opret modeller og DbContext:

Opret filen `Models/Product.cs`:
```csharp
namespace ProductApi.Models
{
    public class Product
    {
        public int Id { get; set; }
        public string Name { get; set; }
        public decimal Price { get; set; }
        public int StockQuantity { get; set; }
        public DateTime CreatedAt { get; set; } = DateTime.UtcNow;
    }
}
```

Opret filen `Data/ProductDbContext.cs`:
```csharp
using Microsoft.EntityFrameworkCore;
using ProductApi.Models;

namespace ProductApi.Data
{
    public class ProductDbContext : DbContext
    {
        public ProductDbContext(DbContextOptions<ProductDbContext> options)
            : base(options)
        {
        }

        public DbSet<Product> Products { get; set; }

        protected override void OnModelCreating(ModelBuilder modelBuilder)
        {
            // Seed data
            modelBuilder.Entity<Product>().HasData(
                new Product { Id = 1, Name = "Laptop", Price = 8999, StockQuantity = 10 },
                new Product { Id = 2, Name = "Smartphone", Price = 5499, StockQuantity = 25 },
                new Product { Id = 3, Name = "Headphones", Price = 1299, StockQuantity = 50 }
            );
        }
    }
}
```
4. Installer 
   ```bash
   dotnet add package Swashbuckle.AspNetCore
   ```
5. Opdater Program.cs for at konfigurere databasen:
```csharp
using Microsoft.EntityFrameworkCore;
using ProductApi.Data;

var builder = WebApplication.CreateBuilder(args);

// Add services to the container.
builder.Services.AddControllers();
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

// Add database context
var connectionString = builder.Configuration.GetConnectionString("DefaultConnection");
builder.Services.AddDbContext<ProductDbContext>(options =>
    options.UseSqlServer(connectionString));

var app = builder.Build();

// Configure the HTTP request pipeline.
app.UseSwagger();
app.UseSwaggerUI();

app.UseHttpsRedirection();
app.UseAuthorization();
app.MapControllers();

// Ensure database is created
using (var scope = app.Services.CreateScope())
{
    var services = scope.ServiceProvider;
    var dbContext = services.GetRequiredService<ProductDbContext>();
    dbContext.Database.EnsureCreated();
}

app.Run();
```

6. Opdater appsettings.json for at tilføje database forbindelsen:
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=db;Database=ProductDb;User=sa;Password=P@ssw0rd123;TrustServerCertificate=True"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "Kestrel": {
    "Endpoints": {
      "Http": {
        "Url": "http://0.0.0.0:80"
      }
    }
  }
}
```

7. Opret en controller til at håndtere produkter:

Opret filen `Controllers/ProductsController.cs`:
```csharp
using Microsoft.AspNetCore.Mvc;
using Microsoft.EntityFrameworkCore;
using ProductApi.Data;
using ProductApi.Models;

namespace ProductApi.Controllers
{
    [ApiController]
    [Route("api/[controller]")]
    public class ProductsController : ControllerBase
    {
        private readonly ProductDbContext _context;

        public ProductsController(ProductDbContext context)
        {
            _context = context;
        }

        // GET: api/products
        [HttpGet]
        public async Task<ActionResult<IEnumerable<Product>>> GetProducts()
        {
            return await _context.Products.ToListAsync();
        }

        // GET: api/products/5
        [HttpGet("{id}")]
        public async Task<ActionResult<Product>> GetProduct(int id)
        {
            var product = await _context.Products.FindAsync(id);

            if (product == null)
            {
                return NotFound();
            }

            return product;
        }

        // POST: api/products
        [HttpPost]
        public async Task<ActionResult<Product>> CreateProduct(Product product)
        {
            _context.Products.Add(product);
            await _context.SaveChangesAsync();

            return CreatedAtAction(nameof(GetProduct), new { id = product.Id }, product);
        }

        // PUT: api/products/5
        [HttpPut("{id}")]
        public async Task<IActionResult> UpdateProduct(int id, Product product)
        {
            if (id != product.Id)
            {
                return BadRequest();
            }

            _context.Entry(product).State = EntityState.Modified;

            try
            {
                await _context.SaveChangesAsync();
            }
            catch (DbUpdateConcurrencyException)
            {
                if (!_context.Products.Any(e => e.Id == id))
                {
                    return NotFound();
                }
                else
                {
                    throw;
                }
            }

            return NoContent();
        }

        // DELETE: api/products/5
        [HttpDelete("{id}")]
        public async Task<IActionResult> DeleteProduct(int id)
        {
            var product = await _context.Products.FindAsync(id);
            if (product == null)
            {
                return NotFound();
            }

            _context.Products.Remove(product);
            await _context.SaveChangesAsync();

            return NoContent();
        }
    }
}
```

8. Opret Dockerfile til API'et (placer i ProductApi-mappen):
```Dockerfile
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

COPY *.csproj ./
RUN dotnet restore

COPY . .
RUN dotnet publish -c Release -o /app/publish /p:UseAppHost=false

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS final
WORKDIR /app
COPY --from=build /app/publish .
EXPOSE 80
ENTRYPOINT ["dotnet", "ProductApi.dll"]
```

9. Gå tilbage til hovedmappen og opret docker-compose.yml:
```yaml
version: '3.8'

services:
  api:
    build: 
      context: ./ProductApi
    ports:
      - "8080:80"
    depends_on:
      - db
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
    networks:
      - product-network
    restart: always

  db:
    image: mcr.microsoft.com/mssql/server:2019-latest
    ports:
      - "1433:1433"
    environment:
      - ACCEPT_EULA=Y
      - SA_PASSWORD=P@ssw0rd123
    volumes:
      - sqldata:/var/opt/mssql
    networks:
      - product-network
    restart: always

networks:
  product-network:
    driver: bridge

volumes:
  sqldata:
    driver: local
```

10. Start applikationen:
```bash
docker-compose up --build
```

11. Test API'et ved at gå til http://localhost:8080/swagger/index.html i browseren

---

## Del 2: Eksperimentér med Docker Compose funktioner 
Vælg mindst to af følgende opgaver:

### A. Tilføj en web frontend
1. Opret en enkel HTML+JavaScript frontend, der viser produkterne
2. Tilføj den som en container i docker-compose.yml

### B. Implementer miljøvariabler
1. Flyt hardcodede værdier som database password til miljøvariabler
2. Opret en .env fil og brug den i docker-compose.yml

### C. Skalering af API-service
1. Ændre docker-compose.yml for at understøtte flere instanser af API'et
2. Test skalering med `docker-compose up --scale api=3`

### D. Implementer et admin dashboard
1. Tilføj Adminer eller phpMyAdmin som en service i docker-compose.yml
2. Brug det til at inspicere og ændre data i databasen

### E. Monitoring
1. Tilføj en simpel health-check endpoint til API'et
2. Konfigurer health checks i docker-compose.yml

---

## Afslutning og Forberedelse

Snak i grupper om jeres løsning:

1. Demonstrer systemets funktionalitet
2. Forklar hvordan Docker Compose hjælper med at organisere de forskellige containere
3. Beskriv hvilke yderligere funktioner I implementerede

---

## Ressourcer
- [Docker Compose Dokumentation](https://docs.docker.com/compose/)
- [Entity Framework Core med SQL Server](https://learn.microsoft.com/en-us/ef/core/providers/sql-server/)
- [SQL Server i Docker](https://learn.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker)