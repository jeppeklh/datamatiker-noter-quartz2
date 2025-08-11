> [!tldr] Definition
> **Express** er et populært webframework til Node.js, der gør det lettere og hurtigere at opbygge servere end ved at bruge Node's indbyggede `http`-modul direkte.
  
- Tilbyder en enklere syntaks og abstraktioner.
- Automatisk håndtering af mange standardopgaver (fx `Content-Type`).
- Bruger stadig [[Node.js]] i bunden.

---
## Eksempel
Serveren her svarer med HTML på `/` og JSON på `/api/notes`:

```js
const express = require('express');
const app = express();

let notes = [
  { id: "1", content: "HTML is easy", important: true },
  { id: "2", content: "Browser can execute only JavaScript", important: false },
  { id: "3", content: "GET and POST are the most important methods of HTTP protocol", important: true }
];

app.get('/', (request, response) => {
  response.send('<h1>Hello World!</h1>');
});

app.get('/api/notes', (request, response) => {
  response.json(notes);
});

const PORT = 3001;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

> [!important] Vigtigt
> - `app.get(path, handler)` definerer en route for HTTP GET-forespørgsler.
   >  
> - `response.send()` sender HTML- eller tekstsvar.
  >   
> - `response.json()` sender automatisk JSON (ingen `JSON.stringify()` nødvendig).
 >    
> - Express sætter selv `Content-Type`-headeren ud fra svaret.
 >    
> - JSON er **et dataformat** og adskiller sig fra JavaScript-objekter, selvom de kan ligne hinanden.

---

## Hvornår bruge Express frem for Node's http-modul?

- Når applikationen vokser, og man vil undgå manuel håndtering af headers, parsing osv.
    
- Når man vil have en mere læsbar og vedligeholdbar kodebase.