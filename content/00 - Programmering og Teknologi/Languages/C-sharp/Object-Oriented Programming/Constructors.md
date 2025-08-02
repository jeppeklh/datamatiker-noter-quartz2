tags: #C-sharp #Programmering #OOP #Methods #Constructors

> [!tldr] Definition
> Constructors are special [[Methods Overview|methods]] in a [[Classes|class]] that are called when an [[Objects|object]] of the [[Classes|class]] is [[Instantiation|instantiated]]. They are used to [[Objects#Object Initialization|initialize]] [[Objects|objects]].

---

## Syntax
Constructors have the same name as the [[Classes|class]] and do not have a [[Return Values|return type]].

---

### Example
```csharp
public class Person 
{ 
	private string name; 
	// Constructor 
	public Person(string name) 
	{
		this.name = name; } 
		public void Greet() 
		{ 
			 Console.WriteLine("Hello, my name is " + name); 
		} 
	}
}
```

---

## Types of Constructors
##### Default Constructor
A constructor that takes no parameters.
```csharp
public Person()
{
    name = "Unknown";
}
```

---

##### Parameterized Constructor
A constructor that takes parameters.
```csharp
public Person(string name)
{
    this.name = name;
}
```

---

##### Static Constructor
A constructor used to initialize static fields of the class.
```csharp
static Person()
{
    // Initialization code
}
```

---

## Usage
Constructors are essential for setting initial values and ensuring that an [[Objects|object]] starts its life in a consistent state

---

## Related Topics
- [[Classes]]
- [[Objects]]
- [[Nedarvning|Inheritance]]
- [[Polymorfi|Polymorphism]]
- [[Indkapsling|Encapsulation]]

---

## Resources
- [Official Documentation on Constructors](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/constructors)
