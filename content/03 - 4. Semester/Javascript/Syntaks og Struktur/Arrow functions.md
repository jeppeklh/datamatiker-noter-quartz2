> [!tldr] Definition  
> Arrow functions er kompakte funktioner i JavaScript uden egen binding til `this`, `arguments` eller `super`.  
> Velegnet til korte funktioner, men **bør ikke** bruges som metoder eller konstruktører.

---

## Key Characteristics
- En arrow function er en alternativ syntaks til en **funktionel expression**.
    
- Den har **ingen egen binding til `this`, `arguments` eller `super`**.
    
- Kan **ikke bruges som constructor** (giver `TypeError` ved `new`).
    
- Understøtter ikke `yield` og kan ikke være generatorfunktioner.
    
---

### Example: basic arrow function
```js
const materials = ["Hydrogen", "Helium", "Lithium", "Beryllium"];

console.log(materials.map((material) => material.length));
// Forventet output: [8, 6, 7, 9]
```

## Syntax
---
```js
() => expression
param => expression
(param1, param2) => expression

() => { statements }
(param) => { statements }

(a = 1, b = 2) => expression
({ a, b }) => expression
async (param) => { statements }
```

---

## Omformning fra traditionel funktion
```js
// Traditionel
(function(a) {
  return a + 100;
});

// Arrow version
a => a + 100;
```

---

## Funktionens krop
```js
const square = x => x * x; // implicit return

const sum = (x, y) => {
  return x + y; // eksplicit return
};
```

---

## Typiske anvendelser
#### Array-metoder:
```js
const arr = [1, 2, 3];
const doubled = arr.map(x => x * 2); // [2, 4, 6]
```

#### Promise chains:
```js
promise
  .then(result => {
    // ...
  })
  .catch(error => {
    // ...
  });
```


---
## Parentheser og return
Parentheser **er påkrævet**, hvis der er **ingen, flere eller komplekse parametre**.

Hvis funktionen kun returnerer én værdi, kan `{}` og `return` udelades:
```js
const double = x => x * 2;
```

Ved brug af `{}` kræves eksplicit `return`:
```js
const sum = (a, b) => {
  return a + b;
};
```

---

## Returnering af objekter
Ved returnering af objekter skal objektet pakkes i `()`:

```js
const getObj = () => ({ key: "value" });
```

---

## this og metoder
Arrow functions **bevarer `this` fra det omkringliggende scope**, hvilket gør dem nyttige i fx `setTimeout`:

```js
const obj = {
  count: 10,
  doLater() {
    setTimeout(() => {
      this.count++;
      console.log(this.count);
    }, 300);
  }
};
obj.doLater(); // logger 11
```

Men de **bør ikke bruges som metode**:
```js
const obj = {
  i: 10,
  b: () => console.log(this.i), // this refererer til globalt scope
  c() {
    console.log(this.i); // korrekt this-binding
  }
};
```

---

## Begrænsninger
Kan **ikke bruges med `new`**:

```js
const Foo = () => {};
new Foo(); // TypeError
```

Kan **ikke bruge `yield`**, så de fungerer ikke som generatorer.

`call`, `bind`, og `apply` **ændrer ikke `this`** i en arrow function.

---

## Resourcer
- [Arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)