---
aliases:
  - Cross-Site Request Forgery
---
> [!tldr] Definition
> En form for angreb, hvor en ondsindet aktør forsøger at få en bruger til ufrivilligt at udføre en handling på et websted, hvor brugeren allerede er autentificeret – f.eks. overføre penge, ændre e-mailadresse eller ændre adgangskode.

---

### Hvordan fungerer CSRF?
1. Brugeren logger ind på et websted (fx `bank.dk`) og får en session-cookie, der bekræfter, at brugeren er autentificeret.
    
2. Brugeren besøger derefter en ondsindet side (fx `hacker.dk`), mens sessionen stadig er aktiv.
    
3. `hacker.dk` sender en forespørgsel til `bank.dk` – f.eks. en POST-request til `bank.dk/overfor/`, som automatisk vedhæfter brugerens cookie.
    
4. Hvis `bank.dk` ikke beskytter sig mod CSRF, tror den, at brugeren selv sendte forespørgslen, og handlingen bliver udført.
    
---

### Hvordan beskytter man mod CSRF?
**Cookie-baseret authentication alene beskytter _ikke_ imod CSRF.** Faktisk er cookies ofte grunden til, at CSRF-angreb kan fungere, fordi de automatisk bliver sendt med hver HTTP-request – uanset oprindelsen.

### Metoder til at beskytte sig:

**CSRF-tokens**
- Serveren genererer et unikt token og sender det til klienten (f.eks. som en del af en formular).
	
- Når klienten sender en request, skal tokenet inkluderes.
	
- Hvis tokenet mangler eller er forkert, bliver anmodningen afvist.

**SameSite-cookies**
- Ved at sætte `SameSite=Strict` eller `SameSite=Lax` på cookies, kan man forhindre, at cookies bliver sendt med cross-site requests.
    
- `SameSite=Strict` forhindrer helt cookies i at blive sendt med cross-origin requests.
    
- `SameSite=Lax` tillader cookies i GET-requests, men ikke POST, hvilket giver en vis beskyttelse.
    
- `SameSite=None` kræver `Secure`-flag og bruges kun, når cross-site cookies er nødvendige (f.eks. i nogle SSO-scenarier).