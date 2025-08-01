tags: #C-sharp #Programmering

## Definition 
---
Reading from and writing to files are common operations in C# applications. 
The `System.IO` namespace provides various [[Classes|classes]] and [[Methods Overview|methods]] to handle file I/O operations efficiently.

## Reading Files
---
To read the content of a file, you can use several approaches. 
Common [[Methods Overview|methods]] include `File.ReadAllText`, `File.ReadAllLines`, and `StreamReader`.
### File.ReadAllText
---
This [[Methods Overview|method]] reads the entire file content into a single [[string]].
```csharp 
string content = File.ReadAllText("example.txt"); 
Console.WriteLine(content);
```

### File.ReadAllLines
---
This [[Methods Overview|method]] reads all lines of a file into a [[string]] [[Arrays|array]].
```csharp
string[] lines = File.ReadAllLines("example.txt");
foreach (string line in lines)
{
    Console.WriteLine(line);
}
```
### StreamReader
---
[[Working with Streams#StreamReader|StreamReader]] provides more control over reading operations, such as reading line by line or using specific encodings.
```csharp
using (StreamReader reader = new StreamReader("example.txt"))
{
    string content = reader.ReadToEnd();
    Console.WriteLine(content);
}
```
## Writing Files
---
Writing content to a file can be done using [[Methods Overview|methods]] like `File.WriteAllText`, `File.WriteAllLines`, and `StreamWriter`.

### File.WriteAllText
---
This [[Methods Overview|method]] writes a [[string]] to a file, replacing its contents if it already exists.
```csharp
File.WriteAllText("example.txt", "Hello, World!");
```
### File.WriteAllLines
---
This [[Methods Overview|method]] writes a [[string]] [[Arrays|array]] to a file, with each element as a new line.
```csharp
string[] lines = { "First line", "Second line", "Third line" };
File.WriteAllLines("example.txt", lines);
```
### StreamWriter
---
[[Working with Streams#StreamWriter|StreamWriter]] allows more control over writing operations, such as writing line by line or using specific encodings.
```csharp
using (StreamWriter writer = new StreamWriter("example.txt"))
{
    writer.WriteLine("Hello, World!");
}
```

## Header2
---
- [[Working with Streams]]
- [[File IO Overview]]
- [[Advanced Topics Overview]]


## Related Topics
---
- [[Working with Streams]]
- [[File IO Overview]]
- [[Advanced Topics Overview]]

## Resources
---
- [Official Documentation on File I/O](https://learn.microsoft.com/en-us/dotnet/standard/io/)