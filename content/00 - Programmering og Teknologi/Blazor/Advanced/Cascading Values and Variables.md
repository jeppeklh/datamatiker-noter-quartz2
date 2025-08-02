---
aliases:
  - Cascading Values
  - Cascading Variables
---
> [!tldr] Definition
> Cascading Values and Parameters er en mekanisme i Blazor, der gør det muligt at dele data (værdier) fra en forælderkomponent til dens underkomponenter uden at skulle passere data eksplicit gennem hver enkelt komponent som en parameter. 

Dette er særligt nyttigt, når du har globale data som temaindstillinger, brugerinformation eller konfigurationsdata, som skal tilgås af mange komponenter i dit applikationshierarki.

---

## Hvad er Cascading Values?
En *cascading value* er en værdi, der bliver "cascaderet" (videregivet) ned gennem komponenttræet. Ved at bruge `<CascadingValue>`-komponenten kan du definere en værdi, som alle underkomponenter automatisk kan få adgang til, uden at du behøver at deklarere en parameter i hver enkelt komponent, som videresender værdien.

---

### Eksempel: Simpelt tema
Antag, at du har et simpelt tema, der skal tilgås af flere komponenter:

**Forælderkomponent (fx `MainLayout.razor`):**
```razor
@using Microsoft.AspNetCore.Components

<CascadingValue Value="Theme">
    @Body
</CascadingValue>

@code {
    private string Theme = "dark";
}
```
Her definerer vi en `CascadingValue` som indeholder en streng `"dark"`, som skal tilgås af alle underkomponenter i layoutet.

---

## Hvad er Cascading Parameters?
For at modtage en cascading value i en underkomponent, skal du markere en parameter med attributten `[CascadingParameter]`. Denne parameter bliver derefter automatisk sat til værdien, der er defineret i den nærmeste overliggende `<CascadingValue>`.

---

### Eksempel: Modtag temaet i en underkomponent
**Underkomponent (fx `ChildComponent.razor`):**
```razor
<div class="@(Theme == "dark" ? "dark-mode" : "light-mode")">
    <p>Aktuelt tema: @Theme</p>
</div>

@code {
    [CascadingParameter]
    public string Theme { get; set; }
}
```
I dette eksempel modtager `ChildComponent` temaet, som bliver cascaderet fra forælderkomponenten, og bruger det til at bestemme CSS-klassen samt vise den aktuelle værdi.

---

## Avancerede Eksempler og Brugsscenarier
### Flere Cascading Values
Du kan cascader flere værdier samtidigt. Eksempelvis, hvis du både ønsker at dele et tema og brugerdata:

**Forælderkomponent:**
```razor
@using MyApp.Models

<CascadingValue Value="Theme">
    <CascadingValue Value="CurrentUser">
        @Body
    </CascadingValue>
</CascadingValue>

@code {
    private string Theme = "light";
    private User CurrentUser = new User { Name = "Anna", Role = "Administrator" };
}
```
**Underkomponent:**
```razor
<div class="@(Theme == "dark" ? "dark-mode" : "light-mode")">
    <h3>Bruger: @CurrentUser.Name</h3>
    <p>Rolle: @CurrentUser.Role</p>
</div>

@code {
    [CascadingParameter]
    public string Theme { get; set; }

    [CascadingParameter]
    public User CurrentUser { get; set; }
}
```
Dette eksempel viser, hvordan du kan have flere cascading values, som underkomponenter kan modtage og bruge samtidig.

---

### Brug af Navngivne Cascading Values
Nogle gange kan det være nødvendigt at have flere værdier af samme type. I sådanne tilfælde kan du navngive dine cascading values med attributten `Name`.

**Forælderkomponent:**
```razor
<CascadingValue Name="PrimaryTheme" Value="blue">
    <CascadingValue Name="SecondaryTheme" Value="green">
        @Body
    </CascadingValue>
</CascadingValue>
```

Underkomponent:
```razor
@code {
    [CascadingParameter(Name = "PrimaryTheme")]
    public string PrimaryTheme { get; set; }

    [CascadingParameter(Name = "SecondaryTheme")]
    public string SecondaryTheme { get; set; }
}
```
Med navngivne cascading values kan du præcist styre, hvilken værdi der skal tilknyttes hvilken parameter i dine underkomponenter.

---

## Fordele og Overvejelser
### Fordele:

- **Reducerer Parameter "Boring":** Du slipper for at skulle passere værdier manuelt gennem hver komponent i et dybt hierarki.
- **Centraliseret Datahåndtering:** Det bliver lettere at vedligeholde og ændre globale værdier, da de defineres ét sted.
- **Genbrug:** Underkomponenter kan genbruges i forskellige kontekster uden at ændre deres API, så længe de forventer de nødvendige cascading values.

### Overvejelser:

- **Overeksponering:** Brug cascading values med omtanke. Hvis du cascader for mange værdier, kan det gøre komponentens afhængigheder uklare.
- **Ydelse:** Store objekter eller hyppigt opdaterede værdier kan påvirke ydelsen, hvis de ændres ofte.
- **Debugging:** Fejl i cascading values kan være svære at spore, da værdierne automatisk bliver injiceret og ikke eksplicit passeret som parametre.

---

## Resourcer
- [Blazor WebAssembly Læringsobjekt (CSS)](https://scorm.itslearning.com/data/3289/C20150/ims_import_38/scormcontent/index.html#/lessons/f7bmOmZ3uAO54-8RL8vo0nLmuDnh-MZO)
- [Blazor WebAssembly LinkedIn Kursus (CSS)](https://www.linkedin.com/learning/blazor-webassembly-foundational-skills/css-isolation?resume=false&u=57075649)
