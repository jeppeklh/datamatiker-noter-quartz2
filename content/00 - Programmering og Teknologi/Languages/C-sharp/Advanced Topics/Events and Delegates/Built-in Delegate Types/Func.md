tags: #C-sharp #Programmering #AdvancedTopics #Delegates 

> [!tldr] Definition
> The `Func` [[Delegates|delegate]] represents a [[Methods Overview|method]] that can return a value and can take zero or more input parameters. 
> The last type [[Parameters|parameters]] in `Func` is always the return type.

Is used for [[Methods Overview|methods]] that return a value, such as calculations, data transformations, or any operation that produces a result.

---

## Syntax
```csharp
Func<int> getRandomNumber;
Func<int, string> numberToString;
Func<int, int, int> addNumbers;
```

---

### Example
```csharp
// A Func delegate with no parameters that returns an int
Func<int> getRandomNumber = () => new Random().Next();
int random = getRandomNumber();
Console.WriteLine($"Random number: {random}");

// A Func delegate with one parameter that returns a string
Func<int, string> numberToString = (number) => $"Number: {number}";
string result = numberToString(42);
Console.WriteLine(result);

// A Func delegate with two parameters that returns an int
Func<int, int, int> addNumbers = (a, b) => a + b;
int sum = addNumbers(5, 10);
Console.WriteLine($"Sum: {sum}");
```

---

## Related Topics
- [[Delegates]]
- [[Action]]
- [[Predicate]]

---

## Resources
- Link
- 