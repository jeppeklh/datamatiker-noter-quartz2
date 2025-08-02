tags: #C-sharp #Programmering #Methods #Overloading #Polymorphism

> [!tldr] Definition
> Overloading allows multiple [[Methods Overview|methods]] in the same scope to have the same name but different [[Parameters|parameters]]. 

It is a form of [[Polymorfi|polymorphism]], which enhances the flexibility and readability of code by allowing  [[Methods Overview|methods]]  and [[Constructors|constructors]] to perform similar actions based on their [[Parameters|parameters]].

---

## Method Overloading
Method overloading allows a [[Classes|class]] to have more than one [[Methods Overview|method]] with the same name, as long as their [[Parameters|parameter]] lists are different.

The overloaded [[Methods Overview|methods]] must have a different type or number of [[Parameters|parameters]]. 

The [[Return Values|return type]] of the [[Methods Overview|methods]] can be the same or different, but it is not considered when distinguishing overloaded methods.

---

### Example
```csharp 
public class Example 
{ 
	// Method with one parameter 
	public void Display(int number) 
	{ 
		Console.WriteLine("Number: " + number); 
	} 
	
	// Overloaded method with two parameters 
	public void Display(int number, string text) 
	{ 
		Console.WriteLine("Number: " + number + ", Text: " + text); 
	} 
	
	// Overloaded method with different parameter type 
	public void Display(double number) 
	{
		 Console.WriteLine("Double Number: " + number); 
	}
 }
```

---

## Constructor Overloading
Constructor overloading allows a [[Classes|class]] to have more than one [[Constructors|constructor]] with different [[Parameters|parameters]]. This provides multiple ways to [[Objects#Object Initialization|initialize]] [[Objects|objects]] of the [[Classes|class]].

---

### Example
```csharp
public class Person
{
    private string name;
    private int age;

    // Constructor with one parameter
    public Person(string name)
    {
        this.name = name;
        this.age = 0; // Default age
    }

    // Overloaded constructor with two parameters
    public Person(string name, int age)
    {
        this.name = name;
        this.age = age;
    }

    public void Display()
    {
        Console.WriteLine("Name: " + name + ", Age: " + age);
    }
}
```

---

## Related Topics
- [[Methods Overview]]
- [[Polymorfi|Polymorphism]]
- [[Constructors]]

---

## Resources
- [Official Documentation on Method Overloading](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/methods)
