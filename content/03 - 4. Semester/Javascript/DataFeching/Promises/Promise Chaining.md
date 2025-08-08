> [!tldr] Definition
> Promise-chaining bruges til at udføre asynkrone opgaver sekventielt, hvor resultatet af én `.then` sendes videre til den næste.

- Hver `.then` returnerer et ny [[Promise|promise]].
- Returnerer handleren en værdi, bliver den givet til næste `.then`.
- Returnerer handleren et promise, venter kæden på at den bliver afgjort.

---

## Eksempel

```js
new Promise(resolve => setTimeout(() => resolve(1), 1000))
  .then(result => {
    console.log(result); // 1
    return result * 2;
  })
  .then(result => {
    console.log(result); // 2
    return result * 2;
  })
  .then(result => console.log(result)); // 4
```

---
## Forskellen på chaining og flere handlers

**Ikke chaining – alle får samme resultat**
```js
let p = new Promise(resolve => setTimeout(() => resolve(1), 1000));

p.then(r => console.log(r)); // 1
p.then(r => console.log(r)); // 1
p.then(r => console.log(r)); // 1
```

---
## Returnere en Promise

Hvis en `.then` returnerer et nyt promise, venter kæden på dens resultat.

```js
new Promise(resolve => setTimeout(() => resolve(1), 1000))
  .then(result => {
    return new Promise(resolve => {
      setTimeout(() => resolve(result * 2), 1000);
    });
  })
  .then(result => console.log(result)); // 2 (efter ekstra 1s)
```

---
## Thenables

Objekter med en `.then`-metode behandles som promises.
```js
class Thenable {
  constructor(num) { this.num = num; }
  then(resolve) {
    setTimeout(() => resolve(this.num * 2), 1000);
  }
}

Promise.resolve(1)
  .then(result => new Thenable(result))
  .then(console.log); // 2
```

---
## Best practice

- Returnér altid et promise fra asynkrone handlinger, så kæden kan fortsætte.
    
- Chaining holder koden “flad” og undgår callback-pyramiden.
