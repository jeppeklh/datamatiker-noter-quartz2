---
aliases:
  - JWT
---
> [!tldr] Definition
> Et JWT-token er en signeret JSON-streng, der indeholder brugerens identitet og rettigheder. Det sendes typisk i HTTP-headeren 
>
> Authorization: `Bearer <token>`.
> 
En kompakt selvstændig metode til sikker overførsel af information mellem consumer / producer som et JSON-objekt.

I Blazor-applikationer anvendes JWT tokens typisk til:
- Brugerautentifikation og -autorisation
- Sikker kommunikation mellem klient og server
- Vedligeholdelse af brugersessioner uden at gemme tilstand på serveren

![[JWT.png]]

---

## Relevans for Blazor
- **Autentificering**: Når en bruger logger ind, sender Blazor-appen legitimationsoplysninger til en API, der returnerer et JWT-token.

- **Autorisation**: Tokenet sendes med hver efterfølgende anmodning for at validerer brugerens adgang.

---

### Implementering i Blazor:
- **Tokenlagring**: I Blazor WebAssembly gemmes JWT-tokenet typisk i localStorage eller sessionStorage (men vær opmærksom på XRSF/XSS-risici).
    
- **HttpClient med Token**:
```csharp
// Tilføj token til HTTP-anmodninger
var token = await authService.GetTokenAsync();
httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);
```

---

## Opbygning og Claims
Et JWT token består af tre dele: header, payload og signatur.

**Header**: Angiver algoritmen (f.eks. HS256 eller RSA) og typen (JWT).
**Payload (Claims)**: Indeholder **claims** (påstande) om brugeren, f.eks.:
```json
{
  "sub": "113", // Subject (bruger-ID)
  "name": "Anders And",
  "role": "Admin",
  "exp": 1672444800 // Udløbstidspunkt
}
```
Claims bruges til at bestemme adgangsrettigheder i applikationen.

**Signature**: Sikrer, at tokenet ikke kan ændres uden den hemmelige nøgle.

I Blazor kan du læse claims fra JWT'en via AuthenticationState:
```csharp
var authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
var user = authState.User;
var userId = user.FindFirst(ClaimTypes.NameIdentifier)?.Value; // "sub"-claim
```

---

## Sikkerhedsrisici uden JWT
- Uautoriseret adgang til API-endepunkter.
- Manglende token-validering kan give adgang til følsomme data.

---

## Resourcer
- [Blazor Sikkerhed Læringsobjekt (JWT)](https://scorm.itslearning.com/data/3289/C20150/ims_import_41/scormcontent/index.html#/lessons/QBa2ety4OlmWqSQY5kHHWND_apjt9zis)
- [JWT Youtube Video](https://www.youtube.com/watch?v=K6pwjJ5h0Gg&ab_channel=Udacity)