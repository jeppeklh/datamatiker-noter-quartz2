tags: #C-sharp #Programmering #Datastructure 

> [!tldr] Definition
> Sets are collections of unique elements. 
> They are used to store data without duplicates and support efficient membership tests. 
> They are implemented as `HashSet<T>`. 

---

## Declaration and Initialization
You can declare and initialize sets as follows.

---

### Examples
```csharp
// Declaration and initialization
HashSet<int> numbers = new HashSet<int>();

// Initializing with values
HashSet<int> numbers = new HashSet<int> { 1, 2, 3, 4, 5 };
```

---

## Accessing Elements
Sets do not support indexing, but you can check for the existence of elements.

---

### Examples
```csharp
HashSet<int> numbers = new HashSet<int> { 1, 2, 3, 4, 5 };
bool containsThree = numbers.Contains(3); // True
```

---

## Adding Elements
You can add elements to a set using the `Add` [[Methods Overview|method]].

---

### Examples
```csharp
HashSet<int> numbers = new HashSet<int>();
numbers.Add(1);
numbers.Add(2);
numbers.Add(3);
numbers.Add(3); // Duplicate, will not be added
```

---

## Removing Elements
Elements can be removed from a set using the `Remove` [[Methods Overview|method]].

---

### Examples
```csharp
HashSet<int> numbers = new HashSet<int> { 1, 2, 3, 4, 5 };
numbers.Remove(3); // Removes the element with value 3
```

---

## Related Topics
- [[Arrays]]
- [[Lists]]
- [[Dictionaries]]

---

## Resources
- [Official Documentation on HashSet](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.hashset-1)
- [Official Documentation on Collections](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/collections)