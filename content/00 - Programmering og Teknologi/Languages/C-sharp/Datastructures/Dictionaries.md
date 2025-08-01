---
aliases:
  - Maps
---
tags: #C-sharp #Programmering #Datastructure 

## Overview
---
Dictionaries are collections of key-value pairs. 
They provide fast lookups by key and are used to associate keys with values.
## Declaration and Initialization
---
You can declare and initialize dictionaries in various ways.
### Examples
---
```csharp
// Declaration and initialization
Dictionary<int, string> students = new Dictionary<int, string>();

// Initializing with values
Dictionary<int, string> students = new Dictionary<int, string>
{
    { 1, "John" },
    { 2, "Jane" },
    { 3, "Jim" }
};
```

## Accessing Elements
---
Elements in a dictionary are accessed and modified using their keys.
### Examples
---
```csharp
Dictionary<int, string> students = new Dictionary<int, string>
{
    { 1, "John" },
    { 2, "Jane" },
    { 3, "Jim" }
};

string studentName = students[1]; // Accessing the element with key 1
students[2] = "Janet"; // Modifying the element with key 2
```

## Adding Elements
---
You can add elements to a dictionary using the `Add` [[Methods Overview|method]] or the indexer.
### Examples
---
```csharp
Dictionary<int, string> students = new Dictionary<int, string>();

students.Add(1, "John");
students[2] = "Jane"; // Using indexer
```
## Removing Elements
---
Elements can be removed from a dictionary using the `Remove` [[Methods Overview|method]].
### Examples
---
```csharp
Dictionary<int, string> students = new Dictionary<int, string>
{
    { 1, "John" },
    { 2, "Jane" },
    { 3, "Jim" }
};

students.Remove(2); // Removes the element with key 2
```

## Iterating Through Dictionaries
---
You can iterate through dictionaries using a [[Foreach loop]].
### Examples
---
```csharp
Dictionary<int, string> students = new Dictionary<int, string>
{
    { 1, "John" },
    { 2, "Jane" },
    { 3, "Jim" }
};

foreach (KeyValuePair<int, string> student in students)
{
    Console.WriteLine($"ID: {student.Key}, Name: {student.Value}");
}
```
## Related Topics
---
- [[Arrays]]
- [[Lists]]
- [[Dictionaries]]

## Resources
---
- [Official Documentation on Dictionaries](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2)
- [Official Documentation on Collections](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/collections)