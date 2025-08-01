Stores single characters, such as 'a' or 'B'. Char values are surrounded by single quotes

You can specify a `char` value with:

 A character literal.
```csharp
char myLetter = 'j'; // Outputs j
```
A Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.
```csharp
char myLetter2 = '\u006A'; // Outputs j
```

A hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.
```csharp
char myLetter3 = '\x006A'; // Outputs j
```
## char plus int
Adding a char and [[int]] will give an [[int]] value. 
It will take the ASCII value (number) of the char and add it to the [[int]]. 
```csharp
char myChar = 'j';
Console.WriteLine(myChar + 5); // Outputs 111
```