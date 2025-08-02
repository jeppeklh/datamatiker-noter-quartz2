tags: #C-sharp #Programmering #AdvancedTopics #ExtensionMethods

> [!tldr] Definition
> Extension methods in C# allow you to add new methods to existing types without altering the original type's source code.
> This feature is particularly useful for adding methods to types for which you do not have the source code, such as .NET framework classes or third-party libraries. 

Extension methods are defined as static methods but are called as if they were instance methods on the extended type.

---

## Defining Extension Methods
To define an extension method:

1. Create a static [[Classes|class]] to contain the extension method.

2. Implement the method as a static method, with the first parameter specifying the type to be extended and prefixed with the `this` keyword.

```csharp
public static class StringExtensions
{
    public static int WordCount(this string str)
    {
        return str.Split(new char[] { ' ', '.', '?' }, StringSplitOptions.RemoveEmptyEntries).Length;
    }
}
```

In this example, the `WordCount` method is defined as an extension method for the `string` type. It counts the number of words in a string.

---

## Using Extension Methods
Once defined, extension methods can be called as if they are instance methods on the extended type.
```csharp
string phrase = "Hello world!";
int wordCount = phrase.WordCount();
Console.WriteLine(wordCount);  // Output: 2
```

---

## Benefits of Extension Methods
- **Readability**: Extension methods allow for more readable code by enabling a fluent interface.
- **Maintainability**: They help in organizing helper methods logically without modifying the original type's source code.
- **Reusability**: Extension methods can be reused across different projects and types.

---

## Related Topics
- Link
- 

---

## Resources
- Link
- 