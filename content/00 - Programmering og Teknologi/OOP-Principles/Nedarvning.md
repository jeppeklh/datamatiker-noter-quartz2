---
aliases:
  - inheritance
  - Inheritance
  - nedarvning
  - inherits
---
## Overview
---
OOP principle where a class ([[#Derived class|subclass]]) inherits properties and behaviors from another class 
([[#Base class|superclass]]), promoting code reuse.


## Base class
---
Class from which other [[000 Bergrebsliste#Class|classes]] inherit [[000 Bergrebsliste#Properties|properties]], [[000 Bergrebsliste#Field-variables|fields]], [[Methods Overview|methods]], and members.
Other names: `superclass`


## Derived class
---
Class that inherits [[000 Bergrebsliste#Properties|properties]] and [[Methods Overview|methods]] from a [[#Base class|base class]], extending its functionality.
Other names: `subclass`


## Sealed class
---
[[000 Bergrebsliste#Class|Class]] that cannot be inherited, preventing further extension of its implementation.


## Overriding
---
Implementering af ny version af en metode nedarvet fra en [[#Base class|baseklasse]]

A [[#Derived class|derived class]] must override all [[Abstraktion#Abstract Method|abstract methods]] of an [[Abstraktion#Abstract Class|abstract class]].


## Virtual
---
A virtual [[Methods Overview|method]] in a [[#Base class|base class]] can be redefined in [[#Derived class|derived classes]] using [[#Overriding|override]].
Enabling [[Polymorfi|polymorphic behavior]].

Only [[Methods Overview|methods]] and [[000 Bergrebsliste#Properties|properties]] with the virtual keyword in a [[#Base class|base class]], can be [[#Overriding|overwritten]]
fx. ToString() in the object class: 
```csharp
public virtual string ToString();
```

An [[Abstraktion#Abstract Method|abstract method]] is implicit a virtual method

## Example
---
```csharp
class Vehicle // base class (parent)
{
	public string brand = "Ford"; // Vehicle field
	public void honk()            // Vehicle method
	{
		Console.WriteLine("Tuut, tuut!");
	}
}

class Car : Vehicle // derived class (child)
{
	public string modelName = "Mustang" // Car field
}

class Program
{
	static void Main(string[] args)
	{
		// Create a myCar object
		Car myCar = new Car();
		
		// Call the honk() method (From the Vehicle class) on the myCar object
		myCar.honk();
		
		// Display the value of the brand field (from the Vehicle class) and the
		// value of the modelName from the Car class)
		Console.WriteLine(myCar.brand + " " + myCar.modelName);
	}
}
```
Se https://www.w3schools.com/cs/cs_inheritance.php

## Inheritence in Constructors
---
Inheritance in [[Constructors]] is a feature in C# that allows a [[#Derived class|derived class]] to inherit the [[Constructors|constructor]] of its [[#Base class|base class]]. 
This means that the [[#Derived class|derived class]] can use the [[Constructors|constructor]] of the base class to [[Variables and Assignment#Initialization|initialize]] its own [[Fields|fields]] and [[Properties|properties]]. 
This feature saves a lot of code duplication and makes it easier to create [[#Derived class|derived classes]] that are closely related to their [[#Base class|base classes]].

### Example
---
```csharp
using System;

class Vehicle
{
	public int speed;

	public Vehicle(int speed)
	{
		this.speed = speed;
	}
}

class Car : Vehicle
{
	public string model;

	public Car(int speed, string model) : base(speed)
	{
		this.model = model;
	}
}

class Program
{
	static void Main(string[] args)
	{
		Car car = new Car(60, "Toyota");

		Console.WriteLine("Car Model: {0}, Speed: {1}", car.model, car.speed);
	}
}
```