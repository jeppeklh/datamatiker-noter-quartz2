> [!tldr] Definition
> **Axios** er et populært promise-baseret bibliotek til HTTP-forespørgsler, der bruges som et alternativ til `fetch`. Det er nemmere at bruge og automatisk parser JSON-responser.

---

### Installation

```bash
npm install axios
```

---

### Import og brug

```js
import axios from 'axios'

axios
  .get('http://localhost:3001/notes')
  .then(response => {
    console.log(response.data) // udskriver dataen fra serveren
  })
```

---

### Fordele

- Returnerer en [[Promise]]
- Automatisk JSON-parsing
- Mere læsbar syntaks end `fetch`


---
## Resourcer
- [Axios Fullstackopen](https://fullstackopen.com/en/part2/getting_data_from_server)
