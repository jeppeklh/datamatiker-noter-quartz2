> [!tldr] Definition
Blazor gør det nemt at oprette og validere formularer ved hjælp af indbyggede komponenter og datavalideringsfunktioner. Du kan implementere både synkron og asynkron validering, og definere valideringsregler via dataannotations.



## Grundlæggende Formularopbygning
---
For at oprette en formular i Blazor benyttes `<EditForm>`-komponenten sammen med en model, der repræsenterer formularens data. Her er et eksempel med en `Person`-model:

```razor
<EditForm Model="@person" OnValidSubmit="HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <div>
        <label for="name">Name:</label>
        <InputText id="name" @bind-Value="person.Name" />
        <ValidationMessage For="@(() => person.Name)" />
    </div>

    <div>
        <label for="age">Age:</label>
        <InputNumber id="age" @bind-Value="person.Age" />
        <ValidationMessage For="@(() => person.Age)" />
    </div>

    <button type="submit">Submit</button>
</EditForm>

@code {
    private Person person = new Person();

    private void HandleValidSubmit()
    {
        // Håndter gyldig formularindsendelse her
    }

    public class Person
    {
        [Required]
        public string Name { get; set; }

        [Range(1, 120)]
        public int Age { get; set; }
    }
}
```
I dette eksempel:

- Formularen er bundet til et `person`-objekt.
- Dataannotations som `[Required]` og `[Range]` definerer, at navnet er obligatorisk, og at alderen skal ligge mellem 1 og 120.
- `<ValidationMessage>` viser specifikke fejl for hvert felt, mens `<ValidationSummary>` lister alle fejl.

## Datavalidering med DataAnnotations
---
Blazor understøtter datavalidering gennem dataannotations, som anvendes direkte på model-egenskaber. Nogle almindelige dataannotations er:

- **Required**: Angiver, at en værdi er påkrævet.
- **Range(min, max)**: Angiver, at en værdi skal ligge inden for et bestemt interval.
- **StringLength(max)**: Angiver den maksimale længde af en streng.
- **RegularExpression(pattern)**: Sikrer, at en værdi matcher et givet mønster.
- **EmailAddress**: Angiver, at en værdi skal være en gyldig e-mailadresse.

Disse attributter sikrer, at brugerinput opfylder de definerede krav, før formularen accepteres.


## Asynkron Validering
---
Blazor understøtter også asynkron og brugerdefineret validering ved at implementere `IValidatableObject`-interfacet i din model. Dette gør det muligt at tilføje komplekse valideringsregler, fx:

```csharp
public class Person : IValidatableObject
{
    [Required]
    public string Name { get; set; }

    [Range(1, 120)]
    public int Age { get; set; }

    public IEnumerable<ValidationResult> Validate(ValidationContext validationContext)
    {
        if (Name == "Admin")
        {
            yield return new ValidationResult("Name cannot be 'Admin'.", new[] { nameof(Name) });
        }
    }
}
```
I dette eksempel valideres, at navnet ikke må være "Admin". Sådan kan du tilføje brugerdefinerede regler, der ikke dækkes af standarddataannotations.
## Resources
---
- [Blazor Læringsobjekt (Blazor og Datavalidering)](https://scorm.itslearning.com/data/3289/C20150/ims_import_36/scormcontent/index.html#/lessons/kX8vvu8SilmpsBrmJCHAMn3Ra2phet4Z)
- [Blazor LinkedIn Kursus (Forms and Validation)](https://www.linkedin.com/learning/front-end-web-development-with-dot-net/forms-validation-in-blazor-web-apps?autoSkip=true&resume=false&u=57075649)