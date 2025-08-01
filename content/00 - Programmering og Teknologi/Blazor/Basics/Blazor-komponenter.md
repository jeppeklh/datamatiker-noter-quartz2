> [!tldr] Definition
Genanvendelige enheder i brugergrænsefladen, som kombinerer [[HTML Overview|HTML]]-markup, [[C-sharp|C#]]-kode og [[Razor]]-syntax for at skabe interaktive og dynamiske webapplikationer med .NET.

## Struktur
---
En typisk Blazor-komponent består af følgende dele:

- **HTML Markup:**  
  Definerer den visuelle struktur og layout for komponenten.

- **C#-Kode:**  
  Indeholder logikken, der håndterer brugerinteraktioner, datahåndtering osv.

- **[[Razor]]-Syntax:**  
  Anvendes til at binde data og logik til [[HTML Overview|HTML]]-markupen, så man kan skrive [[C-sharp|C#]]-kode direkte i HTML.

## Eksempel på en Blazor-komponent
---
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

Denne komponent fungerer som en simpel tæller. 
Når du navigerer til URL'en `/counter`, vises en overskrift ("Counter"), den aktuelle tællerværdi og en knap. Ved at klikke på knappen kaldes metoden `IncrementCount`, som øger tælleren med 1, hvilket demonstrerer både data binding og event handling.


## Brug
---
Det tidligere eksempel ville være gemt i en `.razor`-fil. Navnet på denne fil kunne være `Counter.razor`. Vi kan så genanvende denne komponent i en anden fil ved en HTML-lignende syntax
```HTML
<Counter></Counter>
```
Bemærk at `Counter` er skrevet med stort. Dette lave en instans af `Counter`-komponenten, med al dens implementede kode.

### Komponent-parametre
---
Lad os sige vi gerne vil kunne angive hvor meget vores counter inkremeres med, for hvert click. Dette kunne vi gøre ved at definiere en kompenentparameter. Dette gøres ved hjælp af `[Parameter]`-attributten. 
```razor
@page "/counter"

<h3>Counter</h3>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;
    
    [Parameter]
	public int IncrementAmount { get; set; } = 1
	
    private void IncrementCount()
    {
        currentCount += ImcrementAmount;
    }
}
```
Nu kan parameteren så angives i vores custum HTML-tag
```HTML
<Counter IncrementAmount="2"/>
```
## Nøglefunktioner i Blazor-komponenter
---
- **Genanvendelighed:**  
    Komponenter kan genbruges på tværs af forskellige dele af applikationen, hvilket fremmer modularitet og reducerer kode-duplicering.

- **Komposition:**  
    Muligheden for at indlejre komponenter i andre komponenter gør det nemt at opbygge komplekse UI'er ved at kombinere mindre, fokuserede enheder.

- **Data Binding:**  
    Understøtter både en-vejs og to-vejs data binding, så data automatisk synkroniseres mellem UI og C#-kode.

- **Event Handling:**  
    Gør det muligt at reagere på brugerinteraktioner som klik og input ved hjælp af C#-metoder.


## Fordele ved at bruge Blazor-komponenter
---
- **Produktivitet:**  
    Den modulære struktur og genanvendelighed øger udviklingshastigheden og gør vedligeholdelse lettere.

- **Ydeevne:**  
    Komponenterne er optimeret til høj ydeevne, hvilket giver en responsiv brugeroplevelse.

- **Integration:**  
    Nem integration med andre .NET-biblioteker og -tjenester, hvilket udvider mulighederne for funktionalitet.

## Resourcer
---
- [Blazor Læringsobjekt (Komponenter)](https://scorm.itslearning.com/data/3289/C20150/ims_import_36/scormcontent/index.html#/lessons/pejgar8Y8CpHBkppjUrW7PO4_TCE-9WX)
- [Blazor LinkedIn Kursus (Components)](https://www.linkedin.com/learning/front-end-web-development-with-dot-net/introducing-blazor-components?resume=false&u=57075649)
