> [!tldr] Definition
> Et **Hook** er en funktion i React, der lader dig bruge funktionalitet som state og sideeffekter i funktionelle komponenter. Eksempler: [[useState Hook|useState]], [[Effect Hooks|useEffect]], `useRef`, m.fl.

```js
import { useState } from "react";

function Example() {
  const [count, setCount] = useState(0);
  return <p>{count}</p>;
}
```

---

## Regler for Hooks

Hooks skal altid kaldes på en bestemt måde for at React kan holde styr på deres rækkefølge. Følg disse regler:

#### Tilladt
Hooks skal kaldes direkte i toppen af en funktionel komponent eller en custom hook:
```js
function App() {
  const [name, setName] = useState("Juha");
  const [age, setAge] = useState(0);

  return <div>{name} er {age} år</div>;
}
```

#### Ikke tilladt
Hooks **må ikke** kaldes:
- inde i betingelser (`if`)
- inde i loops
- inde i indlejrede funktioner

Eksempler på forkerte steder:
```js
function App() {
  const [age, setAge] = useState(0);

  if (age > 10) {
    // ulovligt
    const [foo, setFoo] = useState(null);
  }

  for (let i = 0; i < age; i++) {
    // ulovligt
    const [bar, setBar] = useState(false);
  }

  function someHandler() {
    // ulovligt
    const [baz, setBaz] = useState("nope");
  }

  return <div>Eksempel</div>;
}
```


---

### Hvorfor disse regler?

React skal kunne kalde hooks i **samme rækkefølge hver gang** komponenten rendres. Hvis rækkefølgen ændres (fx pga. `if` eller `for`), går Reacts interne hook-mekanik i stykker og giver uforudsigelig opførsel.