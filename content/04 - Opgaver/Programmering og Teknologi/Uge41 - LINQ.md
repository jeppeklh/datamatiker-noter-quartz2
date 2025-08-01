- denne opgave skal du arbejde mere i dybden med LINQ og dets anvendelse i forskellige sammenhænge.

Du har sikkert allerede lagt mærke til Lambda-udtryk, som kan anvendes stort set alle steder, hvor man bruger delegates; dette vil du se flere varianter af i opgaven.

Derudover finder lambda-udtryk udbredt anvendelse i LINQ (.NET Language-Integrated Query), hvilket du også skal se nærmere på i en senere opgave, når vi har være igennem databaser.

Du kan med fordel genbesøge læringsopbjekterne for Lambda udtryk og Extension methods.

Øvelserne kræver at du henter filen LINQ.zip

Det kan være at skal hente .NET 6.0 eller ændre i solution dependencies.

## LINQ og Lambda-udtryk
---
De to statiske .NET-klasser **Enumerable** og **Queryable** er centrale for LINQ og indeholder en bred vifte af extension-metoder, som kombineret med lambda-udtryk er en kraftfuld og kompakt måde at håndtere klasser, som implementerer de to interfaces IEnumerable og IQueryable.

Du skal i denne øvelse arbejde med nogle få extension-metoder Sum(), Where() og OrderBy() fra Enumerable-klassen.

## Øvelse 1: Terminologi
---
Brug **Ordet rundt** til at reflektere over begreberne 
**Enumerable**
En Collection der implementerer `IEnumerable<T>` interfacet. Det tillader at iterere gennem en sekvens af data med eksempelvis [[Foreach loop|Foreach]] 

Lambda udtryk
Se [[Lambda Expressions|Lambdaudtryk]]

LINQ
Et sæt af metoder og query syntaks integreret i [[C-sharp|C#]] til at lave databaselignene queries på collections (filtrering, sortering osv.)

LINQ Method Syntax 
En måde at skrive LINQ queries på, som bruger extenstion method som  `Where`, `Select`, `OrderBy` osv. på Collections istedet for querylignene SQL syntaks.


Sørg for at alle får mulighed for at tale.

Tidsramme: 20 minutter

## Øvelse 2: Anvendelse af Enumerable.Sum()
---
Metoden GetValueOfProducts() i Order-klassen beregner den samlede værdi af alle produkter i en ordre.

Udfør følgende:

- Refaktorér koden i denne metode, så den anvender extension-metoden Enumerable.Sum() og et passende lambda-udtryk i stedet for en foreach-løkke til at beregne summen af produkternes værdi

Original metode
```csharp
public double GetValueOfProducts()
{
    double valueOfProducts = 0;
    foreach (Product product in _products)
    {
        valueOfProducts += product.Value;
    }
    return valueOfProducts;
	}
```

Refaktoreret metode
```csharp
public double GetValueOfProducts()
{
    return _products.Sum(product => product.Value);
}
```

- Kør testen, og tilret om nødvendigt.

## Øvelse 3: Anvendelse af Enumerable.Where()
---
Udvid Product-klassen med to nye properties AvailableFrom og AvailableTo af typen DateTime, så klassen kommer til at se ud som forneden:

```csharp
public class Product
{
	public string Name { get; set; }
	public double Value { get; set; }
	public DateTime AvailableFrom { get; set; }
	public DateTime AvailableTo { get; set; }
}
```

hvor:

- AvailableFrom angiver fra hvilken dato, produktet er tilgængeligt
- AvailableTo angiver til hvilken dato, produktet er tilgængeligt

Udvid InitializeTest()-metoden i UnitTest1.cs, så de to nye properties bliver initialiseret på følgende måde:

Udfør følgende:

- Overload GetValueOfProducts() med metoden GetValueOfProducts(DateTime date) i Order-klassen, hvor man i parameteren date kan angive den dato, produktværdien skal beregnes for. I den nye overloadede metode, benyt Enumerable.Where() med et passende lambda-udtryk, der samlet kun medtager værdien for produkter, hvis parameteren date ligger i tidsintervallet fra AvailableFrom til AvailableTo.

```csharp
public double GetValueOfProducts(DateTime date)
{
    return _products
        .Where(product => product.AvailableFrom <= date && product.AvailableTo >= date)
        .Sum(product => product.Value);
}
```

- Indsæt nedenstående testmetode i jeres testprojekt:       

```csharp
[TestMethod]

public void GetValueOfProductsByDate_Test()   
{    
Assert.AreEqual(0.0, order.GetValueOfProducts(new DateTime(2024, 2, 28)));
Assert.AreEqual(10.0, order.GetValueOfProducts(new DateTime(2024, 3, 2))); 
Assert.AreEqual(25.0, order.GetValueOfProducts(new DateTime(2024, 3, 3)));
Assert.AreEqual(45.0, order.GetValueOfProducts(new DateTime(2024, 3, 4)));    }  
```



-  Kør testen, og tilret din kode (ikke testen) om nødvendigt.

## Øvelse 4: Anvendelse af Enumerable.OrderBy()
---

Udfør følgende:

- Implementér nu en ny metode SortProductOrderByAvailableTo() i Order-klassen, som sorterer alle ordrens produkter i stigende orden efter datoen i AvailableTo-property. I den nye metode, benyt Enumerable.OrderBy() og et passende lambda-udtryk til at udføre sorteringen

```csharp
public List<Product> SortProductOrderByAvailableTo()
{
    return _products.OrderBy(product => product.AvailableTo).ToList();
}
```

- Indsæt følgende testmetode i testprojektet:

```csharp
[TestMethod]

public void SortByAvailableToTest()
{
List<Product> result = order.SortProductOrderByAvailableTo();
Assert.AreEqual(3, result.Count);
Assert.AreEqual("Smør", result[0].Name);
Assert.AreEqual("Mælk", result[1].Name);
Assert.AreEqual("Pålæg", result[2].Name);
}
```

-     Kør testen, og tilret om nødvendigt.

## Øvelse 5: Mere Sum()
---
Hvordan kan du helt undlade metoden Where() i svaret til øvelse 3 ved i stedet at anvende et passende lambda-udtryk i kaldet til Sum() (_hint: C# ternary conditional operator_)?

- Tilret GetValueOfProducts(DateTime date) fra øvelse 3, så løsningen kun anvender Sum() og ikke Where().
```csharp
public double GetValueOfProducts(DateTime date)
{
    return _products
        .Sum(product => (product.AvailableFrom <= date && product.AvailableTo >= date) ? product.Value : 0);
}
```


- Kør testen, og tilret om nødvendigt.

## Øvelse 6: GetTotalPrice()
---
På samme måde som for GetValueOfProducts skal du også tilrette (overloade) både GetBonus() og GetTotalPrice(), så der tages højde for blandt andet en angivet dato, hvor henholdsvis bonus og total pris skal beregnes for.

Udfør følgende:

- Overload både GetBonus() og GetTotalPrice() med metoderne GetBonus(DateTime date, ``<delegate-type>`` ``<parameter-navn>``) og GetTotalPrice(DateTime date, ``<delegate-type>``
`<parameter-navn>`), hvor man kan angive både dato og bonusberegningen som parametre.

- Indsæt følgende testmetode (bonusberegningen er på 20%):

```csharp
[TestMethod]

public void GetTotalPriceByDate_Test()
{
 Assert.AreEqual(0.0,  order.GetTotalPrice(new DateTime(2024, 2, 28), <bonus>));
 Assert.AreEqual(8.0,  order.GetTotalPrice(new DateTime(2024, 3, 2), <bonus>));
 Assert.AreEqual(20.0, order.GetTotalPrice(new DateTime(2024, 3, 3), <bonus>));
 Assert.AreEqual(36.0, order.GetTotalPrice(new DateTime(2024, 3, 4), <bonus>));
}
```



 Erstat ``<bonus>`` med et lambda-udtryk, der beregner 20% bonus.
Kør testen, og tilret om nødvendigt.

## Øvelse 7: Implementér SortProductOrderBy()
---
I øvelse 4 implementerede du metoden SortProductOrderByAvailableTo() i Order-klassen. Metoden kan kun sortere ud fra Order-property’en AvailableTo. Da Order-klassen indeholder 4 properties, kræver det 4 sorteringsfunktioner for at kunne sortere ud fra en vilkårlig property. I stedet for dette, vil du nu gerne implementere én generel metode SortProductOrderBy(), hvor du som parameter kan angive den property, du vil sortere efter. F.eks.

```csharp
 List<Product> result = order.SortProductOrderBy(x => x.Name);

 List<Product> result = order.SortProductOrderBy(x => x.Value);

 List<Product> result = order.SortProductOrderBy(x => x.AvailableFrom);

 List<Product> result = order.SortProductOrderBy(x => x.AvailableTo);
```

Udfør følgende:

- Implementér sorteringsmetoden SortProductOrderBy() med følgende metode-header:  
```csharp
 List<Product> SortProductOrderBy(Func<Product,object> keySelector)
```
- Lav selv testmetoder, der tester de 4 varianter.
- _Hint: Det kan tænkes, at det kunne være smart med et loop, hvor der benyttes Assert.AreEqual_