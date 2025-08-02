---
aliases:
  - objects
  - Object
  - object
---
tags: #C-sharp #Programmering #OOP #Objects

> [!tldr] Definition
> An object is an [[Instantiation|instance]] of a [[Classes|class]]. It is created from a [[Classes|class]] and represents a specific implementation of the [[Classes|class]]. Objects are the building blocks of an [[Object-Oriented Programming Overview|OOP]] application.

---

## Creating Objects 
Objects are created using the `new` keyword followed by the class name.

---

### Example
```csharp
// Creating an instance of the Person class
Person person1 = new Person();
person1.Name = "John";
person1.Greet(); // Outputs: Hello, my name is John
```

---

## Object Initialization
You can [[Variables and Assignment#Initialization|initialize]] objects using [[Constructors|constructors]], which are special [[Methods Overview|methods]] called when an [[Objects|object]] is [[Instantiation|instantiated]].

---

### Example
```csharp
class Person
{
    // Field
    private string name;

    // Constructor
    public Person(string name)
    {
        this.name = name;
    }

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

// Creating an object using the constructor
Person person1 = new Person("John");
person1.Greet(); // Outputs: Hello, my name is John
```

---

## Related Topics
- [[Classes]]
- [[Constructors]]
- [[Nedarvning|Inheritance]]
- [[Polymorfi|Polymorphism]]
- [[Indkapsling|Encapsulation]]

---

## Resources
- [Official Documentation on Objects](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/objects)