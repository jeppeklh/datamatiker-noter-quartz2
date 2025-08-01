For at sikre en Blazor-app kombineres to teknologi:

1. [[Cross-Origin Resource Sharing|CORS]]: Begræns API-adgang til kun tilladte domæner (fx din Blazor-apps domæne).
2. [[JSON Web Tokens|JWT]]: Valider tokenets signatur, issuer, audience og udløbsdato på serveren.

```csharp
services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
  .AddJwtBearer(options => {
    options.TokenValidationParameters = new TokenValidationParameters {
      ValidateIssuer = true,
      ValidateAudience = true,
      ValidIssuer = "https://api.example.com",
      ValidAudience = "https://blazor-app.com",
      IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes("hemmelig_nøgle"))
    };
  });
```

1. **HTTPS**: Brug altid HTTPS til at kryptere kommunikationen mellem Blazor-app og API.
2. **Tokenbeskyttelse**: Undgå at eksponere JWT-tokens i URLs eller logfiler.


## Hyppige Fejl i Blazor
---
- **For slap CORS-konfiguration**: AllowAnyOrigin() eller AllowAnyMethod() kan åbne for angreb.
- **Usikker tokenlagring**: Gemmer tokens i usikret localStorage uden XSS-beskyttelse.
- **Manglende token-validering**: Serveren validerer ikke tokenets signatur eller udløbstid.

## Hvor gemmes JWT i Blazor
---
Hvor JWT tokens gemmes afhænger af Blazor-arkitekturen: localStorage i WebAssembly og cookies/server-side i Blazor Server.

- **Blazor WebAssembly** (client-side):  
    JWTs gemmes typisk i **browserens localStorage** eller sessionStorage via JavaScript-interop:
```csharp
    // Gem token
await JSRuntime.InvokeVoidAsync("localStorage.setItem", "authToken", jwtToken);

// Hent token
var token = await JSRuntime.InvokeAsync<string>("localStorage.getItem", "authToken");
```

- **Blazor Server** (server-side):  
    JWTs gemmes normalt ikke på serveren, da forbindelsen er stateful via SignalR. Tokenet kan overføres via:
    
    - **Cookies** (sikret med HttpOnly, _SameSite=Strict_).
    - **AuthenticationStateProvider**, der validerer tokenet ved hver anmodning.


## Typisk Flow i Blazor
---
1. Brugeren logger ind, og serveren returnerer en JWT.
    
2. Klienten gemmer tokenet i localStorage (WebAssembly) eller sender det som en cookie (Server).
    
3. Ved hver API-anmodning sendes tokenet i Authorization-headeren:
```csharp
httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer",jwtToken);
```

4. Serveren validerer tokenet og anvender claims til autorisering.