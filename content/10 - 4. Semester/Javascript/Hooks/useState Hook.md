> [!tldr] Definition
`useState` er en React Hook, som bruges til at oprette og håndtere komponentens lokale state.

## Syntax
---
```js
const [state, setState] = useState(initialValue);
```

- `state`: den aktuelle værdi.
- `setState`: funktion til at opdatere værdien.
- `initialValue`: startværdien af state.

## Eksempel 1: Counter
---
```js
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Du har klikket {count} gange</p>
      <button onClick={() => setCount(count + 1)}>Klik mig</button>
    </div>
  );
}
```

## Eksempel 2: Input felt
---
```js
function NameInput() {
  const [name, setName] = useState("");

  return (
    <div>
      <input 
        type="text" 
        value={name}
        onChange={(e) => setName(e.target.value)}
      />
      <p>Hej, {name}</p>
    </div>
  );
}
```

## Husk
---
- `useState` kan kun bruges i funktionelle komponenter.

- Du kan have flere `useState` i én komponent.

## Resourcer
---
- [State Documentation](https://react.dev/learn/state-a-components-memory)
