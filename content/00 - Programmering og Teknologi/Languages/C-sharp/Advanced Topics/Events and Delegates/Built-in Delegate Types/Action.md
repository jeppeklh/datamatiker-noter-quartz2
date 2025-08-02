tags: #C-sharp #Programmering #AdvancedTopics #Delegates 

> [!tldr] Definition
> The `Action` [[Delegates|delegate]] represents a [[Methods Overview|method]] that performs an action but does not [[Return Values|return a value]]. It can take zero or more input [[Parameters|parameters]].

Is commonly used for [[Methods Overview|methods]] that perform operations like logging, writing to a file, or other side-effect actions without returning a result.

---

## Syntax
```csharp
Action action;
Action<int> actionWithParam;
Action<int, string> actionWithTwoParams;
```

---

### Example
```csharp
// An Action delegate with no parameters
Action greet = () => Console.WriteLine("Hello, World!");
greet();

// An Action delegate with one parameter
Action<int> printNumber = (number) => Console.WriteLine($"Number: {number}");
printNumber(42);

// An Action delegate with two parameters
Action<int, string> printPerson = (age, name) => Console.WriteLine($"Name: {name}, Age: {age}");
printPerson(30, "Alice");
```

---

## Related Topics
- [[Delegates]]
- [[Func]]
- [[Predicate]]

---

## Resources
- Link
- 