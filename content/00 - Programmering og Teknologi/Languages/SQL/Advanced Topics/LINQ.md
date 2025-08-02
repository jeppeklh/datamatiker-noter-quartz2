tags: #C-sharp #Programmering #AdvancedTopics #LINQ

> [!tldr] Definition
>**LINQ** står for **Language Integrated Query**. 
>Det giver mulighed for at skrive forespørgsler på en mere naturlig og intuitiv måde, direkte i dit [[C-sharp|C#]] program.

LINQ er ikke begrænset til at hente [[Data|data]]. 
LINQ giver dig også mulighed for at transformere, filtrere og sortere data på en fleksibel måde. 
Du kan oprette nye objekter baseret på eksisterende data, udføre komplekse beregninger osv. 

Det giver en ensartet syntaks til at arbejde med forskellige typer datakilder, såsom [[Arrays|arrays]], [[Lists|lister]], XML og  databaser.

---

### Anvendelse
###### Arbejde med databaser
LINQ to SQL og Entity Framework gør det nemt at forespørge på data i relationelle databaser.
###### XML-behandling
LINQ to XML giver dig mulighed for at arbejde med XML-data på en mere objektorienteret måde.
###### In-memory-data 
LINQ kan bruges til at forespørge på enhver samling af objekter, såsom lister og arrays.

---

## Syntax
Der findes 2 syntakser at skrive forespørgsler på:
1. **Forespørgselssyntaks (query syntax):** Minder meget om SQL, men integreret i C#. 
```csharp
var query = from person in people
            where person.Age > 18
            orderby person.Name
            select person.Name;
```

2. **Metodebaseret syntaks (method-based syntax):** Bruger metoder som `Where()`, `Select()`, og `OrderBy()`. Dette er ofte brugt sammen med lambda-udtryk.
```csharp
var query = people
            .Where(person => person.Age > 18)
            .OrderBy(person => person.Name)
            .Select(person => person.Name);
```

---

## Eksempel på Liste
Dette eksempel viser, hvordan LINQ bruges til at filtrere en liste med tal.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public class Program
{
    public static void Main()
    {
        List<int> tal = new List<int> { 1, 2, 3, 4, 5 };

        // Find alle tal større end 3
        var result = from t in tal
                     where t > 3
                     select t;

        // Udskriv resultaterne
        foreach (int t in result)
        {
            Console.WriteLine(t);
        }
    }
}
```

Her filtreres listen, og alle tal større end 3 udskrives. LINQ-forespørgslen består af to dele:

- **Query expressions:** Den syntaks, der bruges til at skrive forespørgsler.

- **Standard query operators:** Metoder som [[WHERE Clause|Where]], [[SELECT|Select]], og [[ORDER BY Clause|OrderBy]], der udfører specifikke operationer på data.

---

## LINQ med MSSSQL-database
Når du arbejder med databaser, bruger du ofte LINQ i forbindelse med **Entity Framework** til at mappe tabeller til C#-klasser. Her er et eksempel på at hente kunder fra en specifik by:

```Csharp
using (var context = new DatabaseContext())
{
    var customersInCity = context.Customers
                                 .Where(c => c.City == "Copenhagen")
                                 .Select(c => new { c.CustomerID, c.Name })
                                 .ToList();

    foreach (var customer in customersInCity)
    {
        Console.WriteLine($"ID: {customer.CustomerID}, Name: {customer.Name}");
    }
}
```

Denne forespørgsel filtrerer kunderne baseret på by og vælger kun `CustomerID` og `Name` til output.

---

## Hvorfor bruge LINQ?
###### Mere læselig kode
LINQ-forespørgsler ligner engelsk, hvilket gør koden nemmere at læse og vedligeholde.

###### Færre fejl
Da LINQ valideres ved kompilering, fanger det mange potentielle fejl tidligt.

###### **Fleksibilitet**
Samme syntaks kan bruges til forskellige datakilder.

###### Produktivitet
Reducerer mængden af kode og gør det nemmere at udføre komplekse dataoperationer.

---

## LINQ metoder
![[LINQ metoder.png]]

---

## Related Topics
- Link
- 

---

## Resources
- [LINQ Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_21/scormcontent/index.html#/lessons/QQs0faLh4vkwbiymhZn5iyCgCM1wDIjt)
- [Microsoft Docs on LINQ](https://learn.microsoft.com/en-us/dotnet/csharp/linq/)]
- [Introduction to LINQ YouTube](https://www.youtube.com/watch?v=2AfAkBke9N4&ab_channel=DamienK)
- [LINQ Query Syntax YouTube](https://www.youtube.com/watch?v=mhRsQwEeoeM&t=3s&ab_channel=ProgrammingBasics)