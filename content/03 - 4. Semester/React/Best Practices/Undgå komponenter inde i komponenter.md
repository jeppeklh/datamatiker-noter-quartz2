> [!note] Bemærk
> Komponenter bør altid defineres **uden for** andre komponentfunktioner.

React genopretter funktioner defineret inde i komponenter **ved hvert render**, hvilket forhindrer optimering og kan føre til performanceproblemer.

---
## Forkert 

```js
const App = () => {
  const [value, setValue] = useState(10);

  const Display = (props) => <div>{props.value}</div>; // Forkert

  return <Display value={value} />;
};
```

React ser `Display` som en ny komponent **hver gang** `App` renderes.

## Korrekt

```js
const Display = (props) => <div>{props.value}</div>;

const App = () => {
  const [value, setValue] = useState(10);

  return <Display value={value} />;
};

```

---
## Hvorfor?

- React kan **ikke genbruge** komponenter, der redefineres på hver render.
- Lokal state i indlejrede komponenter kan blive **nulstillet** uventet.
- Det giver **ingen fordele** at definere komponenter indeni andre.

**Tommelregel:**  
Definér altid komponenter på øverste niveau – uden for `App` eller andre komponenter.