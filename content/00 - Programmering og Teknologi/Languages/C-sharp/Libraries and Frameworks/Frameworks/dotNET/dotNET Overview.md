tags: #C-sharp #Programmering #Framework #dotNET

## Definition 
---
.NET is a free, cross-platform, open-source developer platform for building many different types of applications. 

With .NET, you can use multiple languages, editors, and libraries to build for web, mobile, desktop, games, and IoT.
## Key Features
---
- **Cross-platform:** Build and run applications on Windows, macOS, and Linux.
- **Multiple languages:** Write applications in C#, F#, and Visual Basic.
- **Libraries:** Access a rich library of functionality for all areas of application development.
- **Performance:** High performance and scalability for large-scale applications.
- **Open Source:** Developed as an open-source project on GitHub.
## Components
---
- **.NET Core:** A cross-platform framework for building modern, cloud-based, and internet-connected applications.
- **.NET Framework:** The original framework for Windows-based applications.
- **ASP.NET:** A framework for building web applications and services.
- **Xamarin/MAUI:** A framework for building native mobile applications for iOS and Android.
- **Entity Framework:** An ORM (Object-Relational Mapper) for [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database]] access.
- **WPF and Windows Forms:** Frameworks for building Windows desktop applications.


## Example: Hello World in .NET Core
---
Create a new .NET Core console application:
```bash
dotnet new console -n HelloWorld
cd HelloWorld
```

Edit the `Program.cs` file:
```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }
}
```

Run the application:
```bash
dotnet run
```
## Related Topics
---
- Link
- 

## Resources
---
- [Official .NET Documentation](https://docs.microsoft.com/en-us/dotnet/)
- [Getting Started with .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet)
- [GitHub Repository](https://github.com/dotnet/runtime)