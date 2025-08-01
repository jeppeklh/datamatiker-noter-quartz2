---
aliases:
  - Abstraction
  - abstraction
---
## Definition
---
Data abstraction is the process of hiding certain details and showing only essential information to the user.  
Abstraction can be achieved with either [[#Abstract Class|abstract classes]] or interfaces.
## Abstract Class
---
Classes that cannot be instantiated directly and may contain [[#Abstract Method|abstract methods]], serving as blueprints for other classes. (must be overwritten in the [[Nedarvning#Derived class|derived class]])


## Abstract Method
---
Can only be used in an [[#Abstract Class|abstract class]], and it does not have a body. The body is provided by the [[Nedarvning#Derived class|derived class]] ([[Nedarvning|inherited]] from).
A [[Nedarvning#Derived class|subclass]] must [[Nedarvning#Overriding|override]] all abstract methods of an [[#Abstract Class|abstract class]].
An abstract method is implicit a [[Nedarvning#Virtual|virtual]] method

## Example
---

```csharp
abstract class Animal
{
	public abstract void animalSound();
	public void sleep()
	{
		Console.WriteLine("Zzz");
	}
}
```

From the example above, it is not possible to create an object of the Animal Class:
```csharp
Animal myObj = new Animal(); 

// Will generate an error (Cannot create an instance of the abstract class or
// interface 'Animal')
```

This is how you would inherit from Animal
```csharp
//Derived Class (inherit from Animal)
class Pig : Animal
{
	public override void animalSound()
	{
		// The body of animalSound() is provided here
		Console.WriteLine("The pig says: wee wee");
	}
}

class Program
{
	static void Main(string[] args)
	{
		Pig myPig = new Pig(); // Create a Pig object
		myPig.animalSound();   // Call the abstract method
		myPig.sleep();         // Call the regular method
	}
}
```
Se https://www.w3schools.com/cs/cs_abstract.php

## Interface
---
An `interface` is a completely [[#Abstract Class|abstract class]], which can only contain [[#Abstract Method|abstract methods]] and [[000 Bergrebsliste#Properties|properties]] (with empty bodies).
A [[000 Bergrebsliste#Class|class]] that implements the inferface MUST implement the [[Methods Overview|methods]] of the interface as well
#### Example
---
```csharp
// Interface
interface IAnimal 
{
  void animalSound(); // interface method (does not have a body)
}

// Pig "implements" the IAnimal interface
class Pig : IAnimal 
{
  public void animalSound() 
  {
    // The body of animalSound() is provided here
    Console.WriteLine("The pig says: wee wee");
  }
}

class Program 
{
  static void Main(string[] args) 
  {
    Pig myPig = new Pig();  // Create a Pig object
    myPig.animalSound();
  }
}
```
