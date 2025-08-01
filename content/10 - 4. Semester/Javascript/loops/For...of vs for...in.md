|Konstruktion|Itererer over|Typisk brug|
|---|---|---|
|`for...in`|**Nøgler** (keys)|Objekter eller arrays, når du vil have indeks/navne|
|`for...of`|**Værdier** (values)|Arrays, strings, Maps, Sets (iterables)|
## `for...in` – itererer over **nøgler** (keys)
---


```js
const obj = { a: 1, b: 2 };

for (const key in obj) {
  console.log(key);       // a, b
  console.log(obj[key]);  // 1, 2
}

```

**NB:** Bruges ofte til objekter. Den kan også bruges på arrays, men det er sjældent ønsket, fordi rækkefølgen ikke er garanteret.

## `for...of` – itererer over **værdier** (iterables)
---
```js
const arr = [10, 20, 30];

for (const value of arr) {
  console.log(value);  // 10, 20, 30
}
```

**NB:** Virker kun på **iterable** objekter: Arrays, Strings, Maps, Sets, etc.

## Relation til C# `foreach`
---
I C#:
```csharp
foreach (var item in list) {
    Console.WriteLine(item);
}
```

Dette svarer **næsten direkte til** JavaScript's `for...of`:
```js
for (const item of list) {
    console.log(item);
}
```
Begge bruges til at gennemløbe **værdier** i en samling.

`for...in` har ikke nogen direkte pendant i C# – det minder mest om at iterere over property-navne i f.eks. en `Dictionary`.
