tags: #C-sharp #Programmering #OOP 

> [!tldr] Definition
> Instantiation is the process of creating an [[Objects|object]] from a [[Classes|class]]. 
> It is a fundamental concept in [[Object-Oriented Programming Overview|Object-Oriented Programming]], allowing developers to use the class blueprint to create specific instances.

---

## Syntax
To instantiate an object, the `new` keyword is used followed by the [[Classes|class]] name and [[Constructors|constructor]] parameters (if any).

---

### Example
```csharp
// Instantiating a Person object
Person person1 = new Person("John");

```

In this example, `person1` is an instance of the `Person` class, created using the `new` keyword and a [[Constructors|constructor]] that takes a single [[Parameters|parameter]].

---

## Importance of Instantiation
- **Object Creation**: Instantiation is the first step in bringing [[Classes|classes]] to life as objects.
- **Memory Allocation**: It allocates memory for the new [[Objects|object]].
- **Initialization**: [[Constructors]] are called during instantiation to initialize the [[Objects|object]].

---

## Related Topics
- [[Classes]]
- [[Objects]]
- [[Constructors]]

---

## Resources
- [Official Documentation on Instantiation](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/object-oriented/objects#instantiation)
