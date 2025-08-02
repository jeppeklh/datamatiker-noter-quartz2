tags: #C-sharp #Programmering #Methods 
> [!tldr] Definition
> Return values are used to return data from a [[Methods Overview|method]] to the caller. 
> A [[Methods Overview|method]] can return any [[Datatypes|data type]], including custom types and [[Collections|collections]]. 
> If a [[Methods Overview|method]] does not return any value, it is defined with the `void` return type.

---

## Example
```csharp
// Method that returns an integer
public int Square(int number)
{
    return number * number;
}
```

---

## Returning Custom Types
You can also return custom types, like [[Classes|classes]] or structs.
```csharp
class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
}

Person CreatePerson()
{
    return new Person { Name = "John", Age = 25 };
}

// Calling the method
Person p = CreatePerson();
Console.WriteLine(p.Name); // Outputs: John
Console.WriteLine(p.Age); // Outputs: 25
```

---

## Related Topics
- [[Methods Overview]]
- [[Defining Methods]]
- [[Parameters]]
- [[Overloading]]
- [[Recursion]]