tags: #C-sharp #Programmering #FileIO #Streams #StreamReader #StreamWriter

> [!tldr] Definition
> Streams provide a way to handle input and output operations sequentially. 

In C#, streams are used for reading and writing data to various sources, such as files, memory, or network connections. 

The `System.IO` namespace includes [[Classes|classes]] like [[#StreamReader]] and [[#StreamWriter]] for handling these operations.

---

## StreamReader
StreamReader is used to read characters from a byte [[#Definition|stream]] in a particular encoding.
Often used to read text from a file
```csharp
using (StreamReader reader = new StreamReader("example.txt"))
{
    string content = reader.ReadToEnd();
    Console.WriteLine(content);
}
```

---

### Common Methods
- `Read()`: Reads the next character from the input stream.
- `ReadLine()`: Reads a line of characters from the input stream.
- `ReadToEnd()`: Reads all characters from the current position to the end of the stream.
- `Peek()`: Returns the next available character but does not consume it.

---

## StreamWriter
StreamWriter is used to write characters to a [[#Definition|stream]] in a particular encoding.
Often used to write text to a file
```csharp
using (StreamWriter writer = new StreamWriter("example.txt"))
{
    writer.WriteLine("Hello, World!");
}
```

---

### Common Methods
- `Write()`: Writes a [[char|character]] or [[string]] to the stream.
- `WriteLine()`: Writes a line of [[char|characters]] to the stream.
- `Flush()`: Clears all buffers for the current writer and causes any buffered data to be written to the underlying device.
- `Close()`: Closes the `StreamWriter` and the underlying stream.

---

## Related Topics
- [[File IO Overview]]
- [[Reading and Writing Files]]
- [[Advanced Topics Overview]]
- [[Multithreading and Concurrency]]
- [[Error Handling]]

---

## Resources
- [Official Documentation on StreamReader](https://docs.microsoft.com/en-us/dotnet/api/system.io.streamreader)
- [Official Documentation on StreamWriter](https://docs.microsoft.com/en-us/dotnet/api/system.io.streamwriter)
- [Official Documentation on Streams](https://docs.microsoft.com/en-us/dotnet/standard/io/streams)