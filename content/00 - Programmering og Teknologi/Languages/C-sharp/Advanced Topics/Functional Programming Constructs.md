tags: #C-sharp #Programmering #AdvancedTopics #FunctionalProgramming

## Definition
---
Functional programming constructs in C# allow for a more declarative style of coding. These constructs emphasize immutability, higher-order functions, and the use of functions as first-class citizens.

## Higher-Order Functions
---
Functions that take other functions as parameters or return them as results.

```csharp
Func<int, int, int> add = (x, y) => x + y;
Func<int, int> increment = x => add(x, 1);
Console.WriteLine(increment(5)); // Output: 6
```

## Immutability
---
Favoring immutability means avoiding changing state and instead working with immutable data structures.

```csharp
public class ImmutablePoint
{
    public int X { get; }
    public int Y { get; }

    public ImmutablePoint(int x, int y)
    {
        X = x;
        Y = y;
    }

    public ImmutablePoint Move(int dx, int dy)
    {
        return new ImmutablePoint(X + dx, Y + dy);
    }
}

var point = new ImmutablePoint(1, 2);
var movedPoint = point.Move(3, 4);
Console.WriteLine($"Original: ({point.X}, {point.Y}), Moved: ({movedPoint.X}, {movedPoint.Y})");
// Output: Original: (1, 2), Moved: (4, 6)
```

## Expression Trees
---
Expression trees represent code in a tree-like data structure, where each node is an expression.

```csharp
Expression<Func<int, bool>> isEvenExpr = num => num % 2 == 0;
Func<int, bool> isEven = isEvenExpr.Compile();
Console.WriteLine(isEven(4)); // Output: True
```

## Related Topics
---
- [[Advanced Topics Overview]]
- [[Lambda Expressions]]
## Resources
---
- [LINQ and Functional Programming in C#](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/)