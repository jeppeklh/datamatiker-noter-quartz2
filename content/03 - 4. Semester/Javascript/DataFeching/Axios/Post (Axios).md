---
aliases:
  - Post
---
> [!tldr] Definition
> Bruges til at **sende ny data** til serveren (oprette en ressource).

---
## Eksempel

```js
const newNote = { content: "Hej", important: true };

axios.post('http://localhost:3001/notes', newNote)
  .then(response => {
    setNotes(notes.concat(response.data));
  });
```

- Sender et nyt objekt til serveren.
- Serveren returnerer det oprettede objekt (ofte med ID).


