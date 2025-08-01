---
aliases:
  - Field-variables
  - felt-variabler
  - Field
  - Attributes
  - Member-variables
---
tags: #C-sharp #Programmering 

## Overview
---
Field variables are [[Variables and Assignment|variables]] [[Variables and Assignment#Declaration|declared]] at the [[Classes|class]] level in C#. 
They represent the state or data of an [[Objects|object]] and can be accessed throughout the [[Classes|class]].

## Declaration 
---
Fields are [[Variables and Assignment#Declaration|declared]] within a [[Classes|class]] but outside of any [[Methods Overview|method]].

```csharp
public class Person
{
    private string name;
    public int age;
}

```

## Initialization
---
Fields can be [[Variables and Assignment#Initialization|initialized]] when they are [[Variables and Assignment#Declaration|declared]] or within a [[Constructors|constructor]].

```csharp
public class Person
{
    private string name = "John Doe";
    public int age;

    public Person(int personAge)
    {
        age = personAge;
    }
}

```

## Related Topics
---
- [[Properties|CSharp Properties]]
- [[Variables and Assignment]]
- [[Classes]]