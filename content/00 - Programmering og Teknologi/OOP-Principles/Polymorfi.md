---
aliases:
  - Polymorphism
  - polymorphism
  - polymorfi
---
> [!tldr] Definition
> Occurs when we have many classes that are related to each other by [[Nedarvning|inheritance]].

[[Nedarvning|Inheritance]] lets us inherit fields and [[Methods Overview|methods]] from another class. Polymorphism uses those [[Methods Overview|methods]] to perform different tasks. This allows us to perform a single action in different ways.

---

## Example
```csharp
class Animal // Base class (parent) 
{
	public virtual void animalSound()
	{
		Console.WriteLine("The animal makes a sound");
	}
}

class Pig : Animal //Derived class (child)
{
	public override void animalSound() 
	{
		Console.WriteLine("The pig says: wee wee");
	}
}

class Dog : Animal //Derived class (child)
{
	public override void animalSound() 
	{
		Console.WriteLine("The dog says: bow wow");
	}
}

class Program
{
	static void Main(string[] args) 
	{
		Animal myAnimal = new Animal() // Create an Animal object
		Animal myPig = new Pig()       // Create a Pig object
		Animal myDog = new ogg()       // Create a Dog object
		
		myAnimal.animalSound();
		myPig.animalSound();
		myDog.animalSound();
	}
}
```
We [[Nedarvning#Overriding|override]] the [[Methods Overview|method]] animalSound() in the [[Nedarvning#Derived class|derived classes]]. And now the [[Methods Overview|method]] will have a different output depending on the object type. 
![[Polymorfi output.png]]
Se https://www.w3schools.com/cs/cs_polymorphism.php