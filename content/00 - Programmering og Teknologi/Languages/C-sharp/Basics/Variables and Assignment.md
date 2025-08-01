
tags: #C-sharp #Programmering 
## Overview
---
Variables are used to store data that can be used and manipulated throughout your program.

In C#, you need to [[#Variable Declaration|declare]] variables before you can use them. This note covers variable declaration, [[Datatypes|data types]], and assignment in C#.

## Declaration
---
Declaring a variable means to introduce a new variable to the program. You define its [[Datatypes|type]] and its name.
### Syntax
---
```csharp
int age;
string message;
bool isValid;
```

## Initialization
---
To initialize a variable means to assign it an initial value.
### Syntax
---
```csharp
int number = 10;
string message = "Hello, World!";
bool isValid = true;
```

## Variable Scope
---
The scope of a variable defines where it can be accessed within the code. 
Variables can be declared at the [[Classes|class]] level ([[Fields|fields]]) or within [[Methods Overview|methods]] (local variables).

### Examples
---
```csharp
public class Person
{
    // Field (class-level scope)
    private string name;

    public void SetName()
    {
        // Local variable (method-level scope)
        string greeting = "Hello, " + name;
        
        Console.WriteLine(greeting);  
    }
}
```
## Related Topics
---
- [[Syntax|CSharp Syntax]]
- [[Datatypes|CSharp Datatypes]]
- [[Fields|Csharp Fields]]