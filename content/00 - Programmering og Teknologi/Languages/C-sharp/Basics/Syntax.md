tags: #C-sharp #Syntax 

---
> [!note]
> C# syntax is designed to be straightforward and readable, drawing heavily from C and C++ with influences from Java. This section provides an overview of the essential syntax elements.

---

## Comments
#### Singleline comment
```csharp
// This is a single-line comment
```

#### Multi-lined comment
```csharp
/* This is a 
   multi-line comment */
```

---

## Indentation
Proper indentation is essential for readability.
```csharp
for (int i = 0; i < 10; i++)
{
    Console.WriteLine(i);
}
```

---

## Semicolons
Every statement ends with a semicolon `;`.
```csharp
int number = 10;
Console.WriteLine(number);
```

---

## Method Definition
Basic [[Methods Overview|Method]] syntax:
```csharp
void MyMethod()
{
    // Method body
}
```

---

## Class Definition
Basic [[Classes|Class]] syntax:
```csharp
public class MyClass
{
    // Fields, properties, methods, etc.
}
```

---

## Access Modifiers
Common [[Access modifiers|modifiers]]:
[[Access modifiers#public|public]], [[Access modifiers#private|private]], [[Access modifiers#protected|protected]], [[Access modifiers#internal|internal]]
```csharp
public class MyClass
{
    private int myField;

    public void MyMethod()
    {
        // Method body
    }
}
```

---

## Related Topics
- [[Datatypes]]
- [[Variables and Assignment]]
- [[Control Flows|Control Flow]]
- [[Methods Overview|Methods]]
- [[Classes]]
- [[Object-Oriented Programming Overview|OOP]]
