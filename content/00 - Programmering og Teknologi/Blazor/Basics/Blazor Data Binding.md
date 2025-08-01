

Data binding i Blazor er en central funktion, der muliggør synkronisering af data mellem UI-komponenter og C#-kode. Blazor understøtter både en-vejs og to-vejs databinding, hvilket gør det let at opdatere UI'en baseret på ændringer i data og omvendt.

---

## En-vejs Databinding
---
Ved en-vejs databinding vises data fra en model i UI'en, uden at brugeren direkte ændrer disse data. 

```razor
<p>Current time: @DateTime.Now</p>
```
Her vises den aktuelle tid, som opdateres hver gang komponenten renderes.

## To-vejs Databinding
---
To-vejs databinding synkroniserer data mellem UI'en og en model. Dette er særligt nyttigt for inputfelter, hvor brugeren kan ændre værdier. 
```razor
<input @bind="name" />
<p>Hello, @name!</p>

@code {
    private string name;
}
```
I dette eksempel opdateres variablen `name` automatisk, når brugeren indtaster tekst i inputfeltet.

## Binding af Komplekse Objekter
---
Blazor understøtter binding af komplekse objekter, hvilket er nyttigt, når du arbejder med modeller, der indeholder flere egenskaber.
```razor
<EditForm Model="@person">
    <InputText @bind-Value="person.Name" />
    <InputNumber @bind-Value="person.Age" />
</EditForm>

@code {
    private Person person = new Person();

    public class Person
    {
        public string Name { get; set; }
        public int Age { get; set; }
    }
}
```
Her bindes inputfelter til `Name` og `Age`-egenskaberne i `Person`-objektet, og ændringer reflekteres direkte i modellen.

## Event Binding
---
Blazor gør det også nemt at binde events til metoder, så UI'en kan opdateres dynamisk.
```razor
<button @onclick="IncrementCount">Click me</button>
<p>Current count: @count</p>

@code {
    private int count = 0;

    private void IncrementCount()
    {
        count++;
    }
}
```
I dette eksempel opdateres `count`-variablen hver gang brugeren klikker på knappen, og den nye værdi vises i UI'en.
## Resourcer
---
- [Blazor Læringsobjekt (Data Binding)](https://scorm.itslearning.com/data/3289/C20150/ims_import_36/scormcontent/index.html#/lessons/bWOeX9C-LFTablQSE9Wm1pOnS-C-1lZb)
- [Blazor LinkedIn Kursus (Data Binding)](https://www.linkedin.com/learning/front-end-web-development-with-dot-net/data-binding-in-blazor-web-apps?autoSkip=true&resume=false&u=57075649)
