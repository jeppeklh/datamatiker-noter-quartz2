tags: #C-sharp #Programmering #Datastructure

## Overview 
---
Lists are dynamic collections that can grow and shrink in size. 
They provide flexibility for adding and removing elements. 
## Declaration and Initialization 
---
You can [[Variables and Assignment#Declaration|declare]] and [[Variables and Assignment#Initialization|initialize]] lists in various ways.

### Examples
---

```csharp
// Declaration and initialization
List<int> numbers = new List<int>();

// Initializing with values
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
```

## Accessing and Modifying Elements
---
Elements in a list can be accessed and modified using their index.
### Examples
---
```csharp
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };

int firstNumber = numbers[0]; // Accessing the first element
numbers[1] = 10; // Modifying the second element

```
## ## Adding Elements
---
You can add elements to a list using the `Add` [[Methods Overview|method]]
### Examples
---
```csharp
List<int> numbers = new List<int>();
numbers.Add(1);
numbers.Add(2);
numbers.Add(3);

// Adding multiple elements at once
numbers.AddRange(new int[] { 4, 5, 6 });
```
## Removing Elements
---
Elements can be removed from a list using [[Methods Overview|methods]] like `Remove` and `RemoveAt`.
### Examples
---
```csharp
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };

numbers.Remove(3); // Removes the element with value 3
numbers.RemoveAt(0); // Removes the first element
```
## Related Topics
---
- [[Arrays]]
- [[Sets]]
- [[Dictionaries]]
## Resources
---
- [Official Documentation on Lists](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1)
- [Official Documentation on Collections](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/collections)