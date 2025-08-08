---
aliases:
  - Patch
---
> [!tldr] Definition
> Bruges til at **opdatere enkelte felter** i en ressource.

---

## Eksempel

```js
axios.patch(`http://localhost:3001/notes/${id}`, { important: true })
  .then(response => {
    setNotes(notes.map(note => note.id === id ? response.data : note));
  });
```

- Sender kun de felter, der skal ændres.
    
- Mere effektivt end [[Put (Axios)|Put]] ved små ændringer.
