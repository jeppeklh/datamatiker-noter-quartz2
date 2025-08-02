> [!tldr] Definition
> Blazor gør det nemt at arbejde med data ved at bruge C#-modeller og tjenester til at håndtere dataoperationer. Ved at benytte [[Dependency Injection]] (DI) kan du nemt "injektere" dine datatjenester i komponenter og implementere [[CRUD]]-funktionalitet.

---

## 1. Definere Modellen
Først opretter du en simpel model, fx en `Product`-model:

```csharp
public class Product
{
    public int Id { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
}
```

---

## 2. Oprette en Data Service
Lav en service, der håndterer CRUD-operationer for `Product`-modellen. Her bruges en liste som en simpel datakilde:
```csharp
public class ProductService
{
    private List<Product> products = new List<Product>();

    public List<Product> GetAllProducts()
    {
        return products;
    }

    public Product GetProductById(int id)
    {
        return products.FirstOrDefault(p => p.Id == id);
    }

    public void AddProduct(Product product)
    {
        product.Id = products.Count > 0 ? products.Max(p => p.Id) + 1 : 1;
        products.Add(product);
    }

    public void UpdateProduct(Product product)
    {
        var existingProduct = GetProductById(product.Id);
        if (existingProduct != null)
        {
            existingProduct.Name = product.Name;
            existingProduct.Price = product.Price;
        }
    }

    public void DeleteProduct(int id)
    {
        var product = GetProductById(id);
        if (product != null)
        {
            products.Remove(product);
        }
    }
}
```

---

## 3. Registrere Tjenesten i DI-Containeren
I `Program.cs` registreres `ProductService` i [[Dependency Injection|dependency injection]]-containeren, så den kan injiceres i dine komponenter:
```csharp
builder.Services.AddSingleton<ProductService>();
```
[[Dependency Injection]] fremmer løs kobling, forbedrer testbarhed og gør det nemt at udskifte implementeringer.

---

## 4. Oprette en Blazor-Komponent til CRUD-Operationer
Her er et eksempel på en Blazor-komponent, der bruger `ProductService` til at udføre CRUD-operationer for produkter:
```razor
@page "/products"
@inject ProductService ProductService

<h3>Product List</h3>

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Price</th>
            <th>Actions</th>
        </tr>
    </thead>
    <tbody>
        @foreach (var product in products)
        {
            <tr>
                <td>@product.Name</td>
                <td>@product.Price</td>
                <td>
                    <button @onclick="() => EditProduct(product.Id)">Edit</button>
                    <button @onclick="() => DeleteProduct(product.Id)">Delete</button>
                </td>
            </tr>
        }
    </tbody>
</table>

<h3>Add/Edit Product</h3>
<EditForm Model="@currentProduct" OnValidSubmit="SaveProduct">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <div>
        <label for="name">Name:</label>
        <InputText id="name" @bind-Value="currentProduct.Name" />
    </div>
    <div>
        <label for="price">Price:</label>
        <InputNumber id="price" @bind-Value="currentProduct.Price" />
    </div>
    <button type="submit">Save</button>
</EditForm>

@code {
    private List<Product> products;
    private Product currentProduct = new Product();

    protected override void OnInitialized()
    {
        products = ProductService.GetAllProducts();
    }

    private void SaveProduct()
    {
        if (currentProduct.Id == 0)
        {
            ProductService.AddProduct(currentProduct);
        }
        else
        {
            ProductService.UpdateProduct(currentProduct);
        }
        currentProduct = new Product();
        products = ProductService.GetAllProducts();
    }

    private void EditProduct(int id)
    {
        currentProduct = ProductService.GetProductById(id);
    }

    private void DeleteProduct(int id)
    {
        ProductService.DeleteProduct(id);
        products = ProductService.GetAllProducts();
    }
}
```
I dette eksempel:
- Vises en liste over produkter i en tabel.
- Brugeren kan redigere eller slette et produkt via tilhørende knapper.
- En formular under tabellen giver mulighed for at tilføje eller opdatere et produkt.
- Når formularen indsendes, bliver dataene valideret og gemt via `ProductService`.

---

## Resourcer
- [Blazor Læringsobjekt (Blazor og Data)](https://scorm.itslearning.com/data/3289/C20150/ims_import_36/scormcontent/index.html#/lessons/q-VuQeN77K9yFSCw5xxedPJTgjETZpTK)
- [Blazor LinkedIn Kursus (Data in Blazor)](https://www.linkedin.com/learning/front-end-web-development-with-dot-net/work-with-data-in-blazor?autoSkip=true&resume=false&u=57075649)