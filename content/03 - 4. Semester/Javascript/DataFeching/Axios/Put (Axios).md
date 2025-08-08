---
aliases:
  - Put
---
> [!tldr] Definition
> Bruges til at **erstatte en eksisterende ressource** fuldstændigt. 
>
>Der angives 2 parametre:
> - En **URL** til den ressource, der skal opdateres  
> - Et [[Objects Javascript|objekt]] med de opdaterede værdier

---
## Example

```js
const toggleImportanceOf = (id) => {
  const url = `http://localhost:3001/notes/${id}`;
  const note = notes.find(n => n.id === id);
  const changedNote = { ...note, important: !note.important };

  axios
    .put(url, changedNote)
    .then(response => {
      setNotes(notes.map(note => note.id === id ? response.data : note));
    });
};
```

- **Find noten**, der skal opdateres, ved hjælp af `find()`.
- **Lav et nyt objekt** med den opdaterede `important`-værdi.
- **Send det til serveren** med `axios.put(url, data)`.
- **Opdater den lokale state** med `setNotes()` og erstat den gamle note med den nye via `map()`.

---

> [!tip] Tip  
> `PUT` erstatter hele objektet på serveren — sørg for at sende hele objektet (ikke kun det ændrede felt).
>
> For mindre ændringer brug [[Put (Axios)|Put]].
