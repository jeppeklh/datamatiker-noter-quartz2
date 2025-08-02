tags: #C-sharp #Programmering #AdvancedTopics #Delegates 

> [!tldr] Definition
> The `Predicate` [[Delegates|delegate]] represents a [[Methods Overview|method]] that defines a set of criteria and determines whether the specified object meets those criteria. 
> 
> It always returns a [[bool|boolean]] value.

`Predicate` is used for [[Methods Overview|methods]] that perform checks or validations, such as filtering [[Lists|lists]], checking conditions, or validating inputs.

---

## Syntax
```csharp
Predicate<int> isEven;
Predicate<string> isNullOrEmpty;
```

---

### Example
```csharp
// A Predicate delegate to check if a number is even
Predicate<int> isEven = (number) => number % 2 == 0;
bool result = isEven(4);
Console.WriteLine($"Is 4 even? {result}");

// A Predicate delegate to check if a string is null or empty
Predicate<string> isNullOrEmpty = (str) => string.IsNullOrEmpty(str);
bool isEmpty = isNullOrEmpty("");
Console.WriteLine($"Is string empty? {isEmpty}");
```

---

## Related Topics
- [[Delegates]]
- [[Action]]
- [[Func]]

---

## Resources
- Link
- 