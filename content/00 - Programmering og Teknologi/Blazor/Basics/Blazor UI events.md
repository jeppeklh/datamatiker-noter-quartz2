> [!tldr] Definition
Blazor gør det nemt at håndtere brugerinteraktioner ved hjælp af events. 
Ved at binde C#-metoder til HTML-elementers events (såsom klik, input, ændringer osv.) kan du reagere på brugerhandlinger og dynamisk opdatere UI'en.

---

## Binding af Events
---
For at binde en event til en metode i Blazor anvender du `@`-syntaksen efterfulgt af eventnavnet. For eksempel:

```razor
<button @onclick="HandleClick">Click me</button>

@code {
    private void HandleClick()
    {
        // Håndter klik-eventet her
    }
}
```
Her kaldes metoden `HandleClick`, når brugeren klikker på knappen.

## Almindelige Events i Blazor
----
Nogle af de mest brugte events inkluderer:

- **@onclick:** Håndterer klik-events.
- **@oninput:** Håndterer input-events, når brugeren indtaster tekst.
- **@onchange:** Håndterer ændrings-events, når værdien af et input-element ændres.
- **@onmouseover:** Håndterer mouseover-events, når musen bevæger sig over et element.
- **@onmouseout:** Håndterer mouseout-events, når musen bevæger sig væk fra et element.
## Eksempel på Event Binding
---
Her er et eksempel, der viser, hvordan en input-event kan håndteres for at opdatere en værdi dynamisk:

```razor
<input @oninput="UpdateValue" />
<p>Current value: @currentValue</p>

@code {
    private string currentValue;

    private void UpdateValue(ChangeEventArgs e)
    {
        currentValue = e.Value.ToString();
    }
}
```
I dette eksempel kaldes metoden `UpdateValue` hver gang brugeren indtaster tekst, og `currentValue` opdateres i overensstemmelse.

## Event Argumenter
---
Når du håndterer events, kan du få adgang til eventargumenter ved hjælp af klasser som `EventArgs` eller dens afledte typer. For eksempel:
```razor
<button @onclick="HandleClick">Click me</button>

@code {
    private void HandleClick(MouseEventArgs e)
    {
        var x = e.ClientX;
        var y = e.ClientY;
        // Arbejd med eventargumenterne her
    }
}
```
Her får du adgang til detaljerede oplysninger om klik-eventet via `MouseEventArgs`.

## Fordele ved Event Handling i Blazor
---
- **Fleksibilitet:** Håndter en bred vifte af events med detaljerede argumenter.
- **Integration:** Problemfri integration med C#-kode og .NET-økosystemet, hvilket forenkler udviklingen af interaktive webapplikationer.
## Resourcer
---
- [Blazor Læringsobjekt (Events)](https://scorm.itslearning.com/data/3289/C20150/ims_import_36/scormcontent/index.html#/lessons/yz8efhpiNOzR1KhCKLMDHHNXNLjh0UMi)
- [Blazor LinkedIn Kursus (UI Events)](https://www.linkedin.com/learning/front-end-web-development-with-dot-net/handling-ui-events-in-blazor-web-apps?resume=false&u=57075649)
