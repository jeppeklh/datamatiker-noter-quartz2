tags: #C-sharp #Programmering #Methods 
## Definition
---
Parameters are used to pass information into [[Methods Overview|methods]]. When defining a [[Methods Overview|method]], you specify the parameters it takes. 

Parameters can be of any [[Datatypes|data type]] and you can define multiple parameters separated by commas.
### Example
---
```csharp
// Method with two parameters
public int Multiply(int x, int y)
{
    return x * y;
}
```
### Parameter Types
---
The default parameter type is called a Value Parameter.
Copies the actual value of an argument into the parameter.

```csharp
void ShowValue(int value)
{
    value = 10;
    Console.WriteLine(value); // Outputs: 10
}
```
##### Reference Parameters
---
Passes a reference to the actual data, allowing the [[Methods Overview|method]] to modify the value of the argument.
```csharp
void ShowReference(ref int value)
{
    value = 10;
}
```
##### Output Parameters
---
Similar to reference parameters, but used to return multiple values from a [[Methods Overview|method]].
```csharp
void GetValues(out int a, out int b)
{
    a = 10;
    b = 20;
}
```

##### Parameter Arrays
---
Allows you to pass a variable number of arguments to a [[Methods Overview|method]].
```csharp
void ShowParams(params int[] numbers)
{
    foreach (int num in numbers)
    {
        Console.WriteLine(num);
    }
}
```
## Related Topics
---
- [[Methods Overview]]
- [[Defining Methods]]
- [[Return Values]]
- [[Overloading]]
- [[Recursion]]

