
> [!note] 
> Node.js har et indbygget **http**-modul, som kan bruges til at lave en simpel webserver uden eksterne pakker.  
> - **CommonJS-moduler** bruges (`require`) i stedet for ES6-moduler (`import`), da Node traditionelt har understøttet dette format.
> - `http.createServer()` opretter en server, der håndterer HTTP-forespørgsler.
> - Svar sendes med `response.writeHead()` (status + headers) og `response.end()` (indhold).

---
## JSON-eksempel
Serveren nedenfor returnerer en hardkodet liste af noter i **JSON-format**:

```js
const http = require('http');

let notes = [
  { id: "1", content: "HTML is easy", important: true },
  { id: "2", content: "Browser can execute only JavaScript", important: false },
  { id: "3", content: "GET and POST are the most important methods of HTTP protocol", important: true }
];

const app = http.createServer((request, response) => {
  response.writeHead(200, { 'Content-Type': 'application/json' });
  response.end(JSON.stringify(notes));
});

const PORT = 3001;
app.listen(PORT);
console.log(`Server running on port ${PORT}`);
```

---

> [!important] Vigtigt
> 
> - **Portkonflikter** opstår, hvis porten allerede er i brug (fejl: `EADDRINUSE`).
   >  
> - `Content-Type: application/json` fortæller klienten, at svaret er JSON.
  >   
> - `JSON.stringify()` bruges til at konvertere JavaScript-objekter til en JSON-streng.
  >   
> - Serveren svarer ens, uanset hvilken URL-sti der bruges (`/`, `/foo/bar`, osv.).

