---
aliases:
  - Property
  - property
---
tags: #C-sharp #Programmering
> [!tldr] Definition
> Properties muliggør det at tilgå en [[Access modifiers#private|private]] værdi uden at komprimere sikkerheden i sine data
> Se [[Indkapsling|Indkapsling]]

They are a combination of [[Methods Overview|methods]] that are used as if they were [[Access modifiers#public|public]] [[Fields]].

---

## Declaration
Properties are declared within a [[Classes|class]], typically with a [[Access modifiers#private|private]] [[Fields|field]] to store the value.

---

### Examples
```csharp
public class Person
{
    private string name;
    public string Name
    {
        get { return name; }
        set { name = value; }
    }
}
```

---

## Auto-Implemented Properties
C# allows you to define properties without a [[Access modifiers#private|private]] [[Fields|field]], using auto-implemented properties.

---

### Examples
```csharp
public class Person 
{ 
	public string Name { get; set; } 
	public int Age { get; set; } 
}
```

---

## Read-Only and Write-Only
Properties can be made read-only or write-only by omitting the set or get accessor, respectively.

---

### Examples
```csharp
public class Person
{
	//Read-Only
    private string name;
    public string Name
    {
        get { return name; }
    }
	//Write-Only
    private int age;
    public int Age
    {
        set { age = value; }
    }
}
```

---

## Property Modifiers
Properties can have [[Access modifiers|access modifiers]], and the access level of the get and set accessors can be different.

---

### Examples
```csharp
public class Person 
{ 
	public string Name { get; private set; } 
	public int Age { private get; set; }
 }
```

---

## Related Topics
- [[Fields|CSharp Fields]]
- [[Variables and Assignment|CSharp Variables]]
- [[Classes|CSharp Classes]]
- [[Indkapsling|CSharp Encapsulation]]


