tags: #Programmering #C-sharp #OOP
## Definition
---
Access modifiers are used to set the access level/visibility for classes, fields, [[Methods Overview|methods]] and properties.
## public
---
Kan ses af alle [[000 Bergrebsliste#Class|klasser]] - også på tværs af projects (assemblies)
Har UML-symbolet: `+`
```csharp
public string color;
```
## private
---
Kan kun ses i samme [[000 Bergrebsliste#Class|klasse]]
Har UML-symbolet: `-`
```csharp
private string model = "Mustang";
```
By default, all members of a class are `private` if you don't specify an access modifier:
```csharp
class Car
{
  string model;  // private
  string year;   // private
}
```
## internal
---
Kan ses af alle [[000 Bergrebsliste#Class|klasser]] - dog ikke i andre projects (assemblies)
Har UML-symbolet: `~`
Er default typen for [[000 Bergrebsliste#Class|klasser]]
```csharp
class Program //internal class
{
    static void Main(string[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```
## protected
---
Kan ses i samme [[000 Bergrebsliste#Class|klasse]] og i [[Nedarvning#Derived class|derived klasser]] (arvede klasser)
Har UML-symbolet: `#`
## protected internal
---
Only code in the same assembly _or_ in a derived class in another assembly can access this type or member.
## private protected
---
 Only code in the same assembly _and_ in the same class or a derived class can access the type or member.