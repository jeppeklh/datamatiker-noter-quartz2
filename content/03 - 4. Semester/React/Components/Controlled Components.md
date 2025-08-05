> [!tldr] Definition
>En _controlled component_ er en formular-komponent i React, hvor **input-værdien styres af komponentens state**. Det giver React fuld kontrol over inputfeltets indhold og gør det nemt at reagere på og validere brugerinput.
>
> Kort sagt: Inputfeltets værdi kommer fra `state`, og ændringer opdaterer `state`. 

---

## Eksempel

```js
import { useState } from 'react';

const App = () => {
  const [newNote, setNewNote] = useState('');

  const handleChange = (event) => {
    setNewNote(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    console.log('Submitted note:', newNote);
    setNewNote('');
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        value={newNote}
        onChange={handleChange}
      />
      <button type="submit">Save</button>
    </form>
  );
};

```

#### Nøglepointer

- `value={newNote}` binder inputfeltet til state.
- `onChange={handleChange}` opdaterer state ved input.
- Inputfeltet er nu **kontrolleret** af React – ikke DOM’en.