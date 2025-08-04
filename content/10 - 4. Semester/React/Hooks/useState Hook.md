> [!tldr] Definition
> `useState` er en React Hook, som bruges til at oprette og håndtere komponentens lokale state.

---
## Syntax

```js
const [state, setState] = useState(initialValue);
```

- `state`: den aktuelle værdi.
- `setState`: funktion til at opdatere værdien.
- `initialValue`: startværdien af state.

---
## Eksempel 1: Counter

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

---
## Eksempel 2: Input felt

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

---

> [!warning] Du må aldrig muterer state direkte!
>React skal kunne detektere ændringer i state for at gen-rendere komponenten korrekt. Det kræver, at man opretter en ny reference i stedet for at ændre den eksisterende. 

#### Korrekt måde

Her oprettes et nyt objekt, hvor de eksisterende værdier kopieres med spread-syntaks:
```js
const handleLeftClick = () => 
  setClicks({ ...clicks, left: clicks.left + 1 });

const handleRightClick = () => 
  setClicks({ ...clicks, right: clicks.right + 1 });
```

#### Forkert måde

Her muteres det oprindelige objekt direkte, hvilket React ikke kan opdage som en ændring
```js
const handleLeftClick = () => {
  clicks.left++;
  setClicks(clicks); // Dette virker ikke som forventet
};
```

#### Hvorfor er det forkert?

Selvom det måske _ser ud til_ at virke, bryder det Reacts princip om _immutability_. Når du direkte ændrer en eksisterende state-variabel og sender den samme reference tilbage med `setState`, opdager React ikke, at noget er ændret – og komponenten re-renders derfor ikke som forventet.

Du skal **altid oprette en ny kopi** af state og kun ændre det, der skal opdateres. Uændrede værdier kopieres med spread (`{ ...state }`).

---
## Husk
- `useState` kan kun bruges i funktionelle komponenter.

- Du kan have flere `useState` i én komponent.

---
## Resourcer
- [State Documentation](https://react.dev/learn/state-a-components-memory)
