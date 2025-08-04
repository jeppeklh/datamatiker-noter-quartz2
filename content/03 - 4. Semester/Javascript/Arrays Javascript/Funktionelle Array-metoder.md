> [!tldr] Definition
> I JavaScript kan arrays behandles på en **funktionel måde** ved hjælp af metoder som `map`, `filter`, `reduce`, `find` osv. Disse metoder tillader dig at skrive **renere**, **mere deklarativ** og **kortfattet** kode – uden brug af `for`-løkker og mutation.


De funktionelle metoder er typisk:

- **Immutables** (ændrer ikke det oprindelige array)
- **Deklarative** (fokuserer på hvad der skal ske, ikke hvordan)
- **Højere-ordensfunktioner** (tager funktioner som argumenter)
    

---

## Higher-Order Functions

> [!tldr] Definition
> En **higher-order function** er en funktion, der enten:
>
> - tager en eller flere funktioner som argument(er)
> - returnerer en funktion

### Eksempel

```js
function greeter(message) {
  return function(name) {
    return `${message}, ${name}`;
  };
}

const sayHello = greeter("Hello");
console.log(sayHello("Alice")); // "Hello, Alice"
```

---
## `.map()`

> [!tldr] Definition
> Transformerer hvert element i et array til et nyt array – samme længde.

### Eksempel

```js
const numbers = [1, 2, 3];
const squared = numbers.map(n => n * n);
console.log(squared); // [1, 4, 9]
```

---

## `.filter()`

> [!tldr] Definition
> Filtrerer elementer i et array baseret på en betingelse.

### Eksempel

```js
const numbers = [1, 2, 3, 4];
const even = numbers.filter(n => n % 2 === 0);
console.log(even); // [2, 4]
```

---

## `.find()`

> [!tldr] Definition
> Returnerer det første element, der opfylder betingelsen. Returnerer `undefined`, hvis ingen findes.

### Eksempel

```js
const users = [{ id: 1 }, { id: 2 }];
const user = users.find(u => u.id === 2);
console.log(user); // { id: 2 }
```

---

## `.reduce()`

> [!tldr] Definition
> Reducerer et array til én værdi ved at kombinere elementerne med en funktion.

### Eksempel

```js
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, n) => acc + n, 0);
console.log(sum); // 10
```