---
aliases:
  - Blazor Pages
  - Blazor Routing
---
> [!tldr] Definition
Blazor understøtter en struktureret måde at opbygge webapplikationer på, hvor navigation, sider og [[Blazor Layout|layouts]] spiller en central rolle. Her gennemgår vi, hvordan routing og pages defineres.

## Routing i Blazor
---
> [!tldr] Definition
Routing i Blazor bruges til at navigere mellem forskellige komponenter baseret på URL'en. En router-komponent håndterer navigationen og bestemmer, hvilken komponent der skal vises for en given URL.

### Definition af en Route
---
For at definere en route i en Blazor-komponent, benytter du `@page`-direktivet efterfulgt af den ønskede URL-sti. Eksempel:

```razor
@page "/counter"

<h3>Counter</h3>
<p>Current count: @currentCount</p>
<button @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        currentCount++;
    }
}

```
I dette eksempel sikrer `@page "/counter"`, at komponenten vises, når brugeren navigerer til `/counter`.
### Routeparameter
Vi kan også angive routeparametre. Dette kan vi gøre ved at have en property i vores komponentfil og angive den som parameter oppe  routen således.
```razor
@page "/counter2"
@page "/counter/{initialCount}"

<h3>Counter</h3>
<p>Current count: @currentCount</p>
<button @onclick="IncrementCount">Click me</button>

<p>InitialCount=@InitialCount</p>

@code {
    private int currentCount = 0;

	[Parameter]
	public string InitialCount { get; set; }
	
    private void IncrementCount()
    {
        currentCount++;
    }
}
```
Bemærk at `InitialCount`-propertien er string, fordi URL'en skal være en string. Kan skrives som `@page "/counter/{initialCount?}"` for at gøre parameteren valgfrig. Ellers er den obligatorisk.

#### Route Constraints
Hvis vi vil have at initialCount-routeparameter kun skal være et tal, kan vi angive det med en contraint.
```razor
@page "/counter/{initialCount:int?}"
```
Dette gøres altså ved et `:`. Nu kan vi også lave vores ``InitialCount``-property om til int.
```csharp
	[Parameter]
	public int InitialCount { get; set; }
```
## Pages i Blazor
---
> [!tldr] Definition
Pages i Blazor er komponenter, der er tilknyttet en bestemt route. De fungerer som sider i en traditionel webapplikation og indeholder både UI og logik.
### Eksempel på en Page-Komponent
```razor
@page "/hello"

<h3>Hello, Blazor!</h3>
<p>Welcome to your first Blazor page.</p>
```
Når brugeren navigerer til `/hello`, vises denne komponent som en side.

## Navigation mellem Pages
---
Blazor tilbyder flere metoder til navigation mellem pages:
### Brug af `<NavLink>`-Komponenten
```razor
<NavLink href="/counter">Go to Counter</NavLink>
```
Dette skaber et hyperlink, som navigerer til `/counter` ved klik.

### Programmatisk Navigation
---
Ved at injicere `NavigationManager`-tjenesten kan du navigere programmatisk:
```razor
@inject NavigationManager Navigation

<button @onclick="NavigateToCounter">Go to Counter</button>

@code {
    private void NavigateToCounter()
    {
        Navigation.NavigateTo("/counter");
    }
}
```
Her navigerer knappen brugeren til `/counter` via C#-kode.

## Resourcer
---
- [Blazor Læringsobjekt (Sider, Routing, og Layout)](https://scorm.itslearning.com/data/3289/C20150/ims_import_36/scormcontent/index.html#/lessons/4pQ8P73TM5_n2DvVQakAKJ0aK-vN8yPt)
- [Blazor LinkedIn (Pages, Routing, and Layout)](https://www.linkedin.com/learning/front-end-web-development-with-dot-net/pages-routing-and-layouts-in-blazor?resume=false&u=57075649)