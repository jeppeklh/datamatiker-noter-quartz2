- Use `if` to specify a block of code to be executed, if a specified condition is true
- Use `else` to specify a block of code to be executed, if the same condition is false
- Use `else if` to specify a new condition to test, if the first condition is false
## Example
#### if
```csharp
if (20 > 18) 
{
  Console.WriteLine("20 is greater than 18");
}
```
#### else
```csharp
int time = 20;
if (time < 18) 
{
  Console.WriteLine("Good day.");
} 
else 
{
  Console.WriteLine("Good evening.");
}
// Outputs "Good evening."
```
#### if-else
```csharp
int time = 22;
if (time < 10) 
{
  Console.WriteLine("Good morning.");
} 
else if (time < 20) 
{
  Console.WriteLine("Good day.");
} 
else 
{
  Console.WriteLine("Good evening.");
}
// Outputs "Good evening."
```

## Ternary Operator
Short-hand of [[#if-else|If-else]]
It can be used to replace multiple lines of code with a single line. It is often used to replace simple [[#if-else|if else]] [[000 Bergrebsliste#Statement|statements]].
#### Syntax
```csharp
variable = (condition) ? expressionTrue :  expressionFalse;
```

```csharp
int time = 20;
if (time < 18) 
{
  Console.WriteLine("Good day.");
} 
else 
{
  Console.WriteLine("Good evening.");
}
```
Is the same as
```csharp
int time = 20;
string result = (time < 18) ? "Good day." : "Good evening.";
Console.WriteLine(result);
```