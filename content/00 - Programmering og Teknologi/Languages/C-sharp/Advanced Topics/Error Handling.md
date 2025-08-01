tags: #C-sharp #Programmering #AdvancedTopics #ErrorHandling #Exception


## Definition 
---
Error handling in C# is primarily done through exceptions, which provide a way to manage and respond to runtime errors. 

By using exceptions, you can write robust code that gracefully handles unexpected conditions and ensures that your application can recover from errors or fail gracefully.
## Key Concepts
---
##### Exception 
An [[Objects|object]] that represents an error or unexpected event. 
##### Try-Catch Block
A block of code that attempts to execute a statement and catches any [[#Exception|exceptions]] that occur. 
##### Finally Block
A block of code that always executes, regardless of whether an [[#Exception|exception]] was thrown or not. 
##### Throw Statement
Used to raise an [[#Exception|exception]] manually.


## Try-Catch
---
A try-catch block is used to handle [[#Exception|exceptions]] that occur during the execution of a block of code.
```csharp 
try 
{ 
	// Code that may cause an exception 
}
catch (ExceptionType ex) 
{ 
	// Code to handle the exception 
}
```
## Finally
---
A finally block is used to execute code regardless of whether an [[#Exception|exception]] was thrown.
```csharp
try
{
    // Code that may cause an exception
}
catch (ExceptionType ex)
{
    // Code to handle the exception
}
finally
{
    // Code that always executes
}
```
## Throw
---
The throw statement is used to raise an [[#Exception|exception]].
```csharp
throw new Exception("An error occurred.");
```

## Custom Exceptions
---
You can create custom [[#Exception|exception]] [[Classes|classes]] to handle specific error conditions in your application.
```csharp
public class CustomException : Exception
{
    public CustomException(string message) : base(message)
    {
    }
}
```

## Best Practices
---
- **Catch Specific Exceptions**: Catch only those exceptions that you can handle, and let others propagate.
- **Clean Up Resources**: Always clean up resources in a finally block or use the `using` statement for automatic cleanup.
- **Avoid Empty Catch Blocks**: Do not swallow exceptions by using empty catch blocks. Always handle or log the exception.
- **Provide Meaningful Messages**: When throwing exceptions, provide meaningful messages to help diagnose the problem.
- **Use Custom Exceptions Judiciously**: Only create custom exceptions when built-in exceptions are not sufficient.
## Related Topics
---
- [[Advanced Topics Overview]]
- [[Generics]]
- [[Multithreading and Concurrency]]

## Resources
---
- [Official Documentation on Error Handling](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/exceptions/)