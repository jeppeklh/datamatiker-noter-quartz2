> [!tldr] Definition
> **Promises** bruges til at håndtere asynkrone operationer i [[00 - JavaScript|JavaScript]], f.eks. [[HTTP Requests|HTTP]]-forespørgsler.
> 
> De giver mulighed for at skrive kode, der reagerer på succes eller fejl, efter en asynkron operation er udført.

### Tre tilstande

1. **Pending** – Operationen er i gang.
2. **Fulfilled** – Operationen lykkedes.
3. **Rejected** – Operationen fejlede.

---

## Eksempel

```js
const promise = axios.get('http://localhost:3001/notes')

promise.then(response => {
  console.log(response.data)
})
```

`axios.get(...)` returnerer et promise. Når data er modtaget (fulfilled), kaldes funktionen i `then`, som udskriver `response.data`.

---

### Chaining

```js
axios
  .get('http://localhost:3001/notes')
  .then(response => {
    const notes = response.data
    console.log(notes)
  })
```

Her kædes `then` direkte på `axios.get(...)`. Når serverens svar modtages, hentes `data` ud og logges. Mere læsevenligt og normalt i praksis.



---
## Resourcer
- [Promise Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)


