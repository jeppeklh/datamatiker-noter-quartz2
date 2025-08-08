> [!tldr] Definition
> Axios er en **promise-baseret HTTP-klient** til [[00 - JavaScript|JavaScript]], som ofte bruges i [[00 - React|React]] til at hente eller sende data til en backend (f.eks. via et [[REST API]]).

---

## Axios-metoder

- [[Put (Axios)|Get]]
- [[Post (Axios)|Post]]
- [[Put (Axios)|Put]]
- [[Patch (Axios)|Patch]]
- [[Delete (Axios)|Delete]]

---
## Installation

```bash
npm install axios
```

---

## Import og brug

```js
import axios from 'axios'

axios
  .get('http://localhost:3001/notes')
  .then(response => {
    console.log(response.data) // udskriver dataen fra serveren
  })
```

---

## Fordele

- Returnerer en [[Promise]]
- Automatisk JSON-parsing
- Mere læsbar syntaks end `fetch`


---
## Resourcer
- [Axios Fullstackopen](https://fullstackopen.com/en/part2/getting_data_from_server)
