---
aliases:
  - Get
---
> [!tldr] Definition
> Bruges til at **hente data** fra serveren (read-only).

---

## Eksempel

```js
axios.get('http://localhost:3001/notes')
  .then(response => {
    setNotes(response.data);
  });
```

- Henter data fra serveren.
- `response.data` indeholder den returnerede JSON.