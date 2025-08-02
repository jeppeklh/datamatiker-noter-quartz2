tags: #Programmering #SQL

> [!tldr] Definition
> Wildcards bliver brugt til at erstatte én eller flere characters i en [[string]].
> De bliver brugt sammen med [[LIKE Operator|LIKE]]-operatoren.
> Like-operatoren bliver brugt i [[WHERE Clause|WHERE]]-klausulen.

---

## Syntax

---

### Example
Returnér alle `Customers` der starter med a:
```SQL
SELECT * FROM Customers  
WHERE CustomerName LIKE 'a%';
```

---

## % Wildcard
Repræsenterer nul, én, eller flere characters.

Returner alle `Customers` der ender med `es`:
```SQL
SELECT * FROM Customers  
WHERE CustomerName LIKE '%es';
```

---

## _ Wildcard
Repræsenterer en enkelt character.
Det kan være alle characters eller tal, men hver `_` repræsenterer 1, og kun 1 character.

Returner alle `Customers` hvor `City` starter med `L` efterfulgt af endhver 3 characters, og slutter med `ondon`:
```SQL
SELECT * FROM Customers  
WHERE City LIKE 'L___on';
```

---

##  [] Wildcard
Returnerer et resultat hvis én af de characterer inden i giver et match

Returner alle `Customers` det starter emd enten `b`, `s`, eller `p`:
```SQL
SELECT * FROM Customers  
WHERE CustomerName LIKE '[bsp]%';
```

---

## - Wildcard
Bruges til at specificere en rækkevide af characters inde i [] wildcarded.

Returnér alle `Customers` der starter med `a`,`b`,`c`,`d`, `e`, eller `f`:
```SQL
SELECT * FROM Customers  
WHERE CustomerName LIKE '[a-f]%';
```

---

## Related Topics
- [[LIKE Operator|LIKE]]
- [[WHERE Clause|WHERE]]
- [[SELECT]]

---

## Resources
- [SQL Wildcards](https://www.w3schools.com/sql/sql_wildcards.asp)
- 