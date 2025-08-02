> [!tldr] Definition
> Strings are used for storing text.
A `string` variable contains a collection of characters surrounded by double quotes
```csharp
string greeting = "Nice to meet you!";
```

## Concatination
The `+` operator can be used between strings to combine them. This is called concatenation

```csharp
string firstName = "John ";
string lastName = "Doe";
string name = firstName + lastName;
Console.WriteLine(name); // Outputs John Doe
```
You can also use the string.Concat() [[Methods Overview|method]]
```csharp
string firstName = "John ";
string lastName = "Doe";
string name = string.Concat(firstName, lastName);
Console.WriteLine(name); // Outputs John Doe
```
#### Adding numbers and strings
```csharp
 string myString = "hello";
 Console.WriteLine(myString + 1); //Outputs hello1
```

## Interpolation
Another option of [[#Concatination|string concatination]], which substitutes values of variables into placeholders in a string. Note that you do not have to worry about spaces, like with concatenation
```csharp
string firstName = "John";
string lastName = "Doe";
string name = $"My full name is: {firstName} {lastName}";
Console.WriteLine(name); // Outputs My full name is: John Doe
```