> [!tldr] Definition
> Du kan definere event handlers som **funktioner der returnerer funktioner**. 
 
F.eks. når du vil sende data med:

```js
const hello = (who) => () => {
  console.log('hello', who);
};

<button onClick={hello('world')}>Say Hello</button>
```

- `hello('world')` returnerer en funktion: `() => console.log('hello', 'world')`
- Denne funktion bliver brugt som `onClick` handler

Dette er nyttigt, når du vil **tilpasse en event handler med argumenter**, men uden at kalde funktionen direkte under render.

---

## Eksempel: Opdatér state med argument

```js
const setToValue = (newValue) => () => {
  console.log('value now', newValue);
  setValue(newValue);
};

<button onClick={setToValue(1000)}>thousand</button>
<button onClick={setToValue(0)}>reset</button>
<button onClick={setToValue(value + 1)}>increment</button>
```

#### Alternativ: Brug `() => ...` direkte
Samme funktionalitet kan skrives uden en funktion-der-returnerer-en-funktion:

```js
const setToValue = (newValue) => {
  console.log('value now', newValue);
  setValue(newValue);
};

<button onClick={() => setToValue(0)}>reset</button>
```
Begge løsninger er korrekte. Det er **et spørgsmål om stil og genbrug**.

---
## Resourcer
- [EventHandling Fullstackopen](https://fullstackopen.com/en/part1/a_more_complex_state_debugging_react_apps)
