
Denne tutorial demonstrerer, hvordan du bruger cascading values og parameters i Blazor til at dele data mellem komponenter, som ikke direkte er i en forælder/barn-relation. Vi bruger et eksempel, hvor antallet af varer i en indkøbskurv skal vises i en header-komponent, selvom ændringerne sker i andre dele af applikationen.

---

## Hvorfor bruge Cascading Values og Parameters?

Normale komponentparametre er begrænset til at dele data mellem en forælder og dens direkte underkomponent. Hvis du vil dele data (f.eks. antallet af varer) med flere komponenter, uden at skulle passere værdien gennem hver enkelt komponent, er cascading values løsningen. Det giver et enkelt sted at gemme og opdatere data, som alle relevante komponenter kan få adgang til.

---

## 1. Opret en Model til Indkøbskurv
---
Først opretter vi en model, der skal holde styr på antallet af varer samt en delegate, som opdaterer antallet, når der tilføjes eller fjernes varer.

**ShoppingCartCountModel.cs**
```csharp
public class ShoppingCartCountModel
{
    // Antallet af varer i indkøbskurven
    public int Count { get; set; }
    
    // Delegate, der kaldes, når antallet ændres
    public Action OnCountChange { get; set; }
}
```
_Hvorfor?_  
Denne model centraliserer antallet af varer og gør det nemt at udløse en opdatering, når ændringer sker i andre komponenter.

## 2. Opsæt Cascading Value i MainLayout
---
MainLayout er et ideelt sted at placere den cascading value, da den typisk indeholder både header-komponenten (der viser indkøbskurv-ikonet) og brødteksten, hvor ændringer i kurven kan ske.

**MainLayout.razor**
```razor
@inherits LayoutComponentBase
@inject IShoppingCartService ShoppingCartService

<CascadingValue Value="@ShoppingCartCountModel" Name="ShoppingCartCountModel">
    <Header />
    @Body
</CascadingValue>

@code {
    // Opretter en instans af modellen
    private ShoppingCartCountModel ShoppingCartCountModel { get; set; }

    protected override void OnInitialized()
    {
        // Initialiser modellen og sæt antallet ud fra shopping cart service
        ShoppingCartCountModel = new ShoppingCartCountModel
        {
            Count = ShoppingCartService.Count()
        };
    }
}
```
_Hvorfor?_  
Ved at placere `<CascadingValue>` omkring både header og body gør vi modellen tilgængelig for 
alle underkomponenter, uden at skulle passere den manuelt gennem parametre.

## 3. Modtag Cascading Value i Header-Komponenten
---
I header-komponenten skal vi modtage den cascading value, så vi kan vise det aktuelle antal varer.

**Header.razor**
```razor
@inject IShoppingCartService ShoppingCartService

<div class="shopping-cart-icon">
    <!-- Tjek om modellen er tilgængelig før visning -->
    @if (ShoppingCartCountModel != null)
    {
        <span>@ShoppingCartCountModel.Count</span>
    }
</div>

@code {
    // Modtag den cascading value med det specifikke navn
    [CascadingParameter(Name = "ShoppingCartCountModel")]
    private ShoppingCartCountModel ShoppingCartCountModel { get; set; }

    protected override void OnInitialized()
    {
        if (ShoppingCartCountModel != null)
        {
            // Opsæt delegate til at opdatere antallet og kun refreshe header-komponenten
            ShoppingCartCountModel.OnCountChange += () =>
            {
                // Hent det nye antal fra service og opdater kun denne komponent
                ShoppingCartCountModel.Count = ShoppingCartService.Count();
                InvokeAsync(StateHasChanged);
            };
        }
    }
}
```
_Hvorfor?_  
Her modtager header-komponenten den delte model og registrerer en delegate, som sørger for, at antallet opdateres, når der sker ændringer i indkøbskurven. Ved at kalde `StateHasChanged` opdateres kun headeren, hvilket undgår unødvendige genindlæsninger af hele applikationen.

## 4. Udløs Opdatering fra Andre Komponenter
---
Når du ændrer indkøbskurvens indhold i andre komponenter (f.eks. på produktsiden eller i produktlisten), skal du sørge for at udløse delegate-opkaldet for at opdatere antallet.

**Eksempel i ProductDetails.razor**
```razor
@inject IShoppingCartService ShoppingCartService

<button @onclick="AddToCart">Tilføj til kurv</button>

@code {
    [CascadingParameter(Name = "ShoppingCartCountModel")]
    private ShoppingCartCountModel ShoppingCartCountModel { get; set; }

    private void AddToCart()
    {
        // Tilføj produktet til kurven
        ShoppingCartService.AddItem(productId);

        // Hvis modellen findes, udløses opdateringen
        ShoppingCartCountModel?.OnCountChange?.Invoke();
    }
}
```
_Hvorfor?_  
Efter en handling (tilføjelse/fjernelse af varer) kaldes `OnCountChange`-delegate for at sikre, at alle komponenter, der lytter til modellen, opdateres med den nye værdi.

## Konklusion
---
Denne tutorial viste, hvordan du:

- **Opretter en central model** til at gemme og opdatere indkøbskurvens antal.
- **Bruger `<CascadingValue>`** i MainLayout for at dele data med både header og andre komponenter.
- **Modtager data i header-komponenten** med `[CascadingParameter]` og opdaterer UI'en via en delegate.
- **Udløser opdateringer** fra andre komponenter, så alle relevante dele af applikationen viser et korrekt antal varer.