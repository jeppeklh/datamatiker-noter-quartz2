> [!tldr] Definition
>Render-tilstande bestemmer, om en komponent skal gengives på serveren, klienten eller en kombination af begge.
>
> `@rendermode` i Blazor bruges til at specificere, hvordan og hvor en komponent skal gengives. 

Med `@rendermode` kan du finjustere, hvordan dine komponenter rendres og interagerer, hvilket hjælper med at optimere både initial indlæsning og den efterfølgende brugeroplevelse.

---

## Typer af Render-Tilstande
- **Static Server:**  
  Komponenter gengives statisk på serveren og er ikke interaktive. Dette er ideelt til generering af statisk HTML-indhold.  
  **Syntaks**: `@rendermode Static`
Dette er defaulten i blazor.

- **Interactive Server:**  
  Komponenter gengives på serveren og er interaktive via Blazor Server. UI-opdateringer håndteres med en realtidsforbindelse (SignalR).  
  **Syntaks**: `@rendermode InteractiveServer`

- **Interactive WebAssembly:**  
  Komponenter gengives på klienten ved hjælp af Blazor WebAssembly, hvilket giver fuld interaktivitet, da hele applikationen kører i browseren.  
  **Syntaks**: `@rendermode InteractiveWebAssembly`

- **Auto:**  
  Komponenter gengives først på serveren for hurtigere initial indlæsning og bliver derefter interaktive på klienten via Blazor WebAssembly.  
  **Syntaks**: `@rendermode Auto`

---

## Eksempel på brug af @rendermode
```razor
@page "/example"
@rendermode InteractiveServer

<h3>Example Component</h3>
<p>This component is rendered interactively on the server.</p>
```
I dette eksempel bliver komponenten gengivet interaktivt på serveren ved hjælp af Blazor Server, hvor SignalR håndterer UI-opdateringer.

---

## Resourcer
- [Blazor Læringsobjekt (Rendertilstande)](https://scorm.itslearning.com/data/3289/C20150/ims_import_36/scormcontent/index.html#/lessons/ISPmo6wI0v9T3EeoKJZYdrEooA0am6u0)
- [Blazor LinkedIn Kursus (Render modes)](https://www.linkedin.com/learning/front-end-web-development-with-dot-net/blazor-component-render-modes?resume=false&u=57075649)