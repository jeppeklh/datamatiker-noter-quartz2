---
aliases:
  - Delete
---
> [!tldr] Definition
> Bruges til at **slette en ressource** fra serveren.

---

## Eksempel

```js
axios.delete(`http://localhost:3001/notes/${id}`)
  .then(() => {
    setNotes(notes.filter(note => note.id !== id));
  });
```

- Sletter et [[Objects Javascript|objekt]] via dets ID.
    
- Du skal selv opdatere state bagefter.

