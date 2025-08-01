---
aliases:
  - Class
  - class
  - classes
---
tags: #C-sharp #Programmering #OOP #Classes

## Definition 
---
A class is a blueprint for creating objects. It defines a type by bundling data and methods that work on the data into one single unit. In C#, classes are the foundation of OOP and provide a way to model real-world entities. 
## Defining a Class
---
A class is defined using the `class` keyword, followed by the class name and a pair of curly braces enclosing its members.

## Example
---
```csharp
public class Person
{
    // Field
    private string name;

    // Property
    public string Name
    {
        get { return name; }
        set { name = value; }
    }

    // Method
    public void Greet()
    {
        Console.WriteLine("Hello, my name is " + name);
    }
}
```

## Members of a Class
---
Classes can contain:

- [[Fields]]: Variables that hold data.
- [[Properties]]: Accessors for [[Fields]].
- [[Methods Overview|Methods]]: Functions that perform operations on the data.

## Related Topics
---
- [[Objects]]
- [[Constructors]]
- [[Nedarvning|Inheritance]]
- [[Polymorfi|Polymorphism]]
- [[Indkapsling|Encapsulation]]

## Resources
---
- [Official Documentation on Classes](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/classes)