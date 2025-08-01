>[!tldr] Definition
MVC er et designmønster, der opdeler en applikation i tre hovedkomponenter:
>
>- **Model**: Håndterer data og forretningslogik.
>- **View**: Ansvarlig for præsentation af data til brugeren.
>- **Controller**: Modtager brugerinput, interagerer med modellen og vælger det rigtige view.

---

Formålet med MVC er at adskille ansvarsområder (Separation of Concerns), hvilket giver:

- **Bedre organisering** af koden
- **Mere vedligeholdelsesvenlig** applikation
- **Øget testbarhed** og fleksibilitet

## Model
---
- **Ansvar**: Repræsenterer data og forretningslogik.
- **Funktioner**: Håndterer dataadgang, validering og forretningsregler.

>[!example] Eksempel 
I en bogapplikation indeholder modellen information om bøger (f.eks. titel, forfatter) samt metoder til at hente og gemme data.

## View
---
- **Ansvar**: Præsenterer data for brugeren.
- **Funktioner**: Genererer brugergrænseflade (ofte [[HTML Overview|HTML]], [[CSS]], JavaScript).

>[!example] Eksempel 
>En webside, der viser en liste over bøger, kan være et view i MVC.

## Controller
---
- **Ansvar**: Fungerer som bindeled mellem Model og View.
- **Funktioner**: Modtager brugerens input (f.eks. via HTTP-anmodninger), interagerer med modellen og vælger det passende view til at vise data.

>[!example] Eksempel 
En controller i en bogapplikation kan håndtere anmodninger om at vise, tilføje eller opdatere bøger.

![[MVC.png]]
# Eksempel på en Simpel MVC-Applikation
---
### Model
```csharp
public class Product
{
    public int Id { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
}
```
### Controller
```csharp
public class ProductController : Controller
{
    public IActionResult Index()
    {
        var product = new Product { Id = 1, Name = "Laptop", Price = 1200.00M };
        return View(product);
    }
}
```
### View (Index.cshtml)
```HTML
@model Product

<h2>@Model.Name</h2>
<p>Price: @Model.Price</p>
```
![[MVCExample.png]]

# MVC i .NET Core
---
I ASP.NET Core MVC bruges MVC-mønstret til at opbygge webapplikationer. Nogle vigtige aspekter:

- **Folderstruktur**: Projekter følger en bestemt struktur, hvor man typisk finder mapper som _Controllers_, _Models_ og _Views_.
- **Razor-syntaks**: Views skrives ofte i Razor, en syntaks der kombinerer [[HTML Overview]] med [[C-sharp|C#]]-kode.
- **Fordele**:
    - Separation of Concerns
    - Øget testbarhed
    - Platformsuafhængighed (kører på Windows, macOS, Linux)
    - Understøttelse af moderne webudviklingspraksis (dependency injection, middleware, routing)

## Resourcer
---
- [MVC Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_31/scormcontent/index.html#/lessons/grhP87jiixA2xco0Po68qgclVO-mlfzn)