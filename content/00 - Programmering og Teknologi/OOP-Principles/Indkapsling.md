---
aliases:
  - Encapsulation
  - encapsulation
  - indkapsling
---
> [!tldr] Definition
> Wrapping up data and information under a single unit.
> Declaring all the [[000 Bergrebsliste#Field-variables|field-variables]] in the class as [[000 Bergrebsliste#Private (-)|private]] and using [[000 Bergrebsliste#Properties|properties]] in the class to [[000 Bergrebsliste#Auto-implemented property|set and get the values]] of variables.

````csharp
public String Name

    {
        get { return studentName; }
        set { studentName = value; }
    }
````

---

## Advantages
#### Testing code is easy 
Encapsulated code is easy to test for unit testing.
#### Hvorfor gøre [[000 Bergrebsliste#Field-variables|felt-variabler]] private?
Så de ikke pludselig kan ændres fra andre [[#Class|klasser]] i koden
#### Flexibility
We can make the variables of the class as read-only or write-only depending on our requirement. If we wish to make the variables as read-only then we have to only use Get Accessor in the code. If we wish to make the variables as write-only then we have to only use Set Accessor.

---

## Resources
- [Encapsulation](https://www.geeksforgeeks.org/c-sharp-encapsulation/)