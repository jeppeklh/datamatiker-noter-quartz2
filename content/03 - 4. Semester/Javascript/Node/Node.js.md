> [!tldr] Definition
> **Node.js** er et JavaScript-runtime, der kører uden for browseren.  
> Det gør det muligt at bruge JavaScript til server-side udvikling, scripts og automatisering.
S
- Bygger på **V8 JavaScript-motoren** (samme som i Google Chrome).
- Bruges ofte til backend-udvikling.
- Har indbygget understøttelse af moduler (CommonJS / ES Modules).
- Kommer med **npm** (Node Package Manager) til håndtering af pakker.

---
## Eksempel

```js
// server.js
const http = require('http');

const server = http.createServer((req, res) => {
  res.end('Hej fra Node.js');
});

server.listen(3000, () => {
  console.log('Server kører på http://localhost:3000');
});
```

---

## Hvornår bruges Node.js?

- Backend API'er
    
- Realtids-applikationer (chat, spil)
    
- Automatisering og scripts
    
- Server-side rendering
