> [!tldr] Definition
> `useEffect` gør det muligt for funktionelle komponenter at udføre sideeffekter – som f.eks. data-fetching, DOM-manipulation, og subscriptions.

Det bruges til at **synkronisere komponenten med eksterne systemer** efter render. 

---

## Syntax

```jsx
useEffect(() => {
  // Effekt-logik
}, [dependencies])
```

- **Effektfunktionen** kører efter første render og efterfølgende renders, hvis afhængighederne ændrer sig.
- Et **tomt array `[]`** betyder, at effekten kun køres én gang (ved første render).
	- Arrayet kaldes **Dependency-list**, og React overvåger de værdier, der står i den. Effekten køres igen, når en af disse værdier ændrer sig.

---
## Eksempel: Data-fetching med Axios

```jsx
import { useState, useEffect } from 'react'
import axios from 'axios'

const App = () => {
  const [notes, setNotes] = useState([])

  useEffect(() => {
    console.log('effect')

    axios.get('http://localhost:3001/notes')
      .then(response => {
        console.log('promise fulfilled')
        setNotes(response.data)
      })
  }, [])

  return (
    <ul>
      {notes.map(note => <li key={note.id}>{note.content}</li>)}
    </ul>
  )
}
```

#### Udførelsesrækkefølge

1. **Første render:** `render 0 notes`
    
2. **Effekt udføres:** `console.log('effect')`
    
3. **Data hentes:** `axios.get(...)`
    
4. **Når data modtages:** `setNotes(response.data)`
    
5. **Komponenten re-renderes:** `render 3 notes`

> [!note] Hvorfor sker der en ny render?
> Når du kalder `setNotes(...)`, opdateres komponentens state. Dette får React til automatisk at **re-rendere komponenten**, så den nye tilstand (fx de hentede noter) vises i UI'et. Det er en grundlæggende del af, hvordan React fungerer: _hver gang state ændres, renderes komponenten igen_ med den nye tilstand.

### Alternativ måde at skrive effekten

```jsx
const hook = () => {
  axios.get('http://localhost:3001/notes')
    .then(response => setNotes(response.data))
}

useEffect(hook, [])
```


---

> [!important] Vigtigt
>- Effekter køres **efter render**.
  >  
>- Brug `[ ]` for kun at køre effekten én gang.
 >   
>- Effektfunktionen kan adskilles for bedre læsbarhed
>
> - Opdatering af state med fx `setNotes(...)` vil **altid føre til re-render** af komponenten.