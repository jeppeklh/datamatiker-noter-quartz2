tags: #C-sharp #Programmering #AdvancedTopics #LambdaExpressions

> [!tldr] Definition
> Lambda expressions in C# provide a concise way to represent anonymous methods. 

They are often used to create [[Delegates|delegates]] or expression tree types. Lambda expressions are particularly useful in writing [[LINQ]] queries.

---

## Syntax
```csharp
(parameters) => expression
(parameters) => { statements }
```

---

## Examples

#### Single-line Lambda Expression
```csharp
Func<int, int> square = x => x * x;
Console.WriteLine(square(5)); // Output: 25
```
#### Multi-line Lambda Expression
---
```csharp
Func<int, int, int> add = (x, y) =>
{
    int result = x + y;
    return result;
};
Console.WriteLine(add(3, 4)); // Output: 7
```

Example 2
```csharp
public class Program
{
	public static void Main()
	{
		Action<int> printEvenOrOdd = (number) =>
		{
			if (number % 2 == 0)
				Console.WriteLine(number + " er lige.");
			else
				Console.WriteLine(number + " er ulige.");
		};
		printEvenOrOdd(5); // Output: 5 er ulige.
		printEvenOrOdd(4); // Output: 4 is lige.
	}
}
```
Hvis Lambda-udtrykket ikke returnerer en værdi som i ovenstående eksempel anvendes delegat typen **Action```<inputtype>```**

---

#### Using Lambda with LINQ
```csharp
int[] numbers = { 2, 5, 10, 8, 1 };
var evenNumbers = numbers.Where(n => n % 2 == 0).ToList();
evenNumbers.ForEach(n => Console.WriteLine(n)); // Output: 2, 10, 8
```

---

## Related Topics
- [[Advanced Topics Overview]]
- [[Functional Programming Constructs]]

---

## Opgaver
- [[Uge34 - Delegates og Lambda Expressions (Svaret).pdf#page=1&selection=0,4,0,4|Uge 34 Opgaver]]

---

## Resources
- [Official C# Documentation - Lambda Expressions](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions)
- [Lambdaudtryk læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_8/scormcontent/index.html#/lessons/_a6KeY2tA66kQMUd7hX1Vs5kcZ6mZyKQ)