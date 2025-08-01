tags: #C-sharp #Programmering #AdvancedTopics #Generics

## Definition 
---
Generics allow you to define [[Classes|classes]], [[Abstraktion#Interface|interfaces]], and [[Methods Overview|methods]] with a placeholder for the [[Datatypes|type of data]] they store and manipulate. 

This promotes code reusability, type safety, and performance by allowing you to create flexible and strongly-typed [[Data Structues Overview|data structures]] and [[Algorithms Overview|algorithms]].

A generic class is declared with a type parameter in angle brackets `<T>`.


## Key Concepts
---
##### Type Parameters
 Placeholder for the actual [[Datatypes|data type]]. For example, `T` in `List<T>`. 

##### [[#Generic Classes|Generic Classes]] and [[#Generic Classes|Methods]]
[[Classes]] and [[Methods Overview|methods]] that operate on type [[Parameters|parameters]]. 

##### [[#Constraints|Constraints]]
Conditions that restrict the [[Datatypes|types]] that can be used as arguments for type [[Parameters|parameters]].



## Syntax
---
### Generic Classes
---
A generic [[Classes|class]] is declared with a type parameter in angle brackets `<T>`.
```csharp
public class GenericClass<T> 
{ 
	private T data; 
	
	public GenericClass(T value) 
	{ 
		data = value; 
	} 
	
	public T GetData() 
	{ 
		return data; 
	} 
}
```

### Generic Methods
---
A generic [[Methods Overview|method]] is declared with a type parameter in angle brackets `<T>` before the [[Return Values|return type]].
```csharp
public class GenericMethodClass
{
    public void Display<T>(T value)
    {
        Console.WriteLine("Value: " + value);
    }
}
```

### Constraints
---
Constraints restrict the [[Datatypes|types]] that can be used as type arguments.
```csharp
public class GenericClass<T> where T : IComparable<T>
{
    public bool Compare(T a, T b)
    {
        return a.CompareTo(b) > 0;
    }
}
```

Here the type argument has to be of a [[Datatypes|type]] that implements the IComparable [[Abstraktion#Interface|interface]] ([[int]], [[bool]], [[string]] etc.)

## Example of using a Generic Class
---
```csharp
class Program
{
    static void Main()
    {
        GenericClass<int> intInstance = new GenericClass<int>(10);
        Console.WriteLine(intInstance.GetData()); // Outputs: 10

        GenericClass<string> stringInstance = new GenericClass<string>("Hello");
        Console.WriteLine(stringInstance.GetData()); // Outputs: Hello
    }
}
```

## Related Topics
---
- [[Advanced Topics Overview]]
- [[Error Handling]]
- [[Multithreading and Concurrency]]

## Resources
---
- [Official Documentation on Generics](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/generics)