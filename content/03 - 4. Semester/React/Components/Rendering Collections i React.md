> [!tldr] Definition
> At **render collections** i React betyder at vise en liste af elementer (fx objekter i et array) som JSX-komponenter ved hjælp af JavaScript – typisk med `map()`.

---

## Eksempel

#### Data

```jsx
const notes = [
  { id: 1, content: 'HTML is easy', important: true },
  { id: 2, content: 'Browser can execute only JavaScript', important: false },
  { id: 3, content: 'GET and POST are the most important methods of HTTP protocol', important: true }
]
```

#### Dynamisk rendering

```jsx
<ul>
  {notes.map(note => 
    <li key={note.id}>
      {note.content}
    </li>
  )}
</ul>
```

> [!warning] Bemærk!
> - JavaScript-udtryk skal være i `{}` i JSX.
> - Brug `key={note.id}` for at undgå warnings og sikre korrekt rendering.

