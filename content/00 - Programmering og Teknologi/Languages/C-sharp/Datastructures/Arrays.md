tags: #C-sharp #Programmering #Datastructure 

> [!tldr] Definition
> Arrays are collections of elements identified by index. 
> They are fixed in size and store elements of the same type. 

---

## Declaration and Initialization
You can [[Variables and Assignment#Declaration|declare]] and [[Variables and Assignment#Initialization|initialize]] arrays in several ways.

---

### Examples
```csharp
// Declaration and initialization
int[] numbers = new int[5];

// Initializing with values
int[] numbers = { 1, 2, 3, 4, 5 };

// Using the new keyword with values
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

---

## Accessing Array Elements
Array elements are accessed using their index, starting from 0.

---

### Examples
```csharp
int[] numbers = { 1, 2, 3, 4, 5 };

int firstNumber = numbers[0]; // Accessing the first element
numbers[1] = 10; // Modifying the second element
```

---

## Multidimentional Arrays
C# supports multidimensional arrays, such as 2D arrays.

---

### Examples
```csharp
int[,] matrix = new int[3, 3];

// Initializing a 2D array
int[,] matrix = { { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };

// Accessing elements
int element = matrix[1, 2]; // Accessing the element in the second row, third column
```

---

## Related Topics
- [[Lists]]
- [[Sets]]
- [[Dictionaries]]

---

## Resources
- [Official Documentation on Arrays](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/)
- [Official Documentation on Collections](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/collections)