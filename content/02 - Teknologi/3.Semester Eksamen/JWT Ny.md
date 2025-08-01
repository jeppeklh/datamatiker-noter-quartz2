## Introduktion til JSON Web Tokens (JWT)

### Hvad er JWT?
---
JSON Web Token (JWT) er en åben standard for en kompakt, URL-sikker token, der gør det muligt at overføre information sikkert som JSON mellem forskellige parter. 

En JWT er digitalt signeret (fx med en hemmelig nøgle ved eller med en privat nøgle), så modtageren kan verificere tokenets integritet og oprindelse. 
JWT anvendes typisk til at bekræfte en brugers identitet mellem en klient (f.eks. en frontend/webapp) og en server, hvilket muliggør sikker autentifikation og autorisation i webapplikationer og API’er. 
Med andre ord kan en JWT fungere som et **digitalt adgangskort**, der indeholder information (claims) om brugeren eller sessionen, og som serveren kan stole på, fordi det er kryptografisk signeret.

**Bemærk:** En JWT er som standard _kun_ Base64URL-kodet, ikke krypteret. Det betyder at indholdet i tokenets payload kan læses af enhver, der dekoder det, om end det ikke kan ændres uden at bryde signaturen. Man bør derfor undgå at placere meget følsomme oplysninger i en JWT, medmindre tokenet også krypteres. Formålet med signaturen er at sikre, at dataene ikke er blevet manipuleret, og at de stammer fra en legitim udsteder.

### Hvordan fungerer JWT? (Struktur og flow)
---
Struktur af en JWT token (JSON Web Token) består af tre dele: **Header**, **Payload** og **Signature**. 

**Header**
Indeholder metadata om tokenet, herunder typen (JWT) og den anvendte signerings-algoritme. 

**Payload**
Indeholder selve informationerne eller _claims_ – dvs. påstande om brugeren eller anden data (f.eks. bruger-ID, navn, roller, udstedelsestidspunkt "`iat`", udløbstid "`exp`"). 

**Signature**
En digital signatur, der skabes ved at tage den Base64-kodede header og payload, og signere dem med en hemmelig nøgle ved hjælp af den angivne algoritme. 

Disse tre dele Base64URL-kodes og sammenføjes med punktum (`.`) imellem til én samlet streng – det endelige JWT-token.

En JWT ser således ud som en lang streng delt op i tre segmenter adskilt af punktummer, fx:

```
xxxxx.yyyyy.zzzzz
```

hvor hver del (xxxxx = header, yyyyy = payload, zzzzz = signature) er Base64URL-kodet data. 

**Eksempel**
For at illustrere indholdet: header kunne fx indeholde `{"alg": "HS256", "typ": "JWT"}`, payload kunne indeholde `{"sub": "12345", "name": "Alice", "exp": 1672531199}`, og signature er en hash-værdi beregnet ud fra header+payload og den hemmelige nøgle.

### JWT autentifikations-flow
---
I praksis bruges JWT ofte til **stateless** autentifikation mellem klient og server. Et typisk flow er som følger:

**Login og token-udstedelse** 
Brugeren logger ind ved at sende sine credentials (f.eks. brugernavn/adgangskode) til serveren. Hvis login-oplysningerne er gyldige, genererer serveren en JWT, der indeholder relevante oplysninger om brugeren (claims) og signerer tokenet med sin hemmelige nøgle. Tokenet indeholder typisk et unikt bruger-ID eller andet der identificerer brugeren, samt evt. brugerens rolle og en udløbstid (`exp`).

**Token til klient** 
Serveren sender den genererede JWT tilbage til klienten som svar på login. Klienten gemmer tokenet – f.eks. i browserens `localStorage` eller i en cookie – på en sikker måde.

**Brug af token ved API-kald** 
Når klienten fremover skal tilgå beskyttede ressourcer eller API-endpoints, sendes JWT med i hver anmodning, typisk i HTTP `Authorization` headeren som en Bearer token: `Authorization: Bearer <JWT>.

**Validering på serveren** 
Serveren modtager anmodningen og kontrollerer JWT’en. Den verificerer først tokenets **signatur** ved hjælp af den kendte hemmelige nøgle eller offentlige nøgle (afhængigt af signeringsmetode) for at sikre, at tokenet er ægte og ikke er blevet ændret undervejs. Dernæst valideres tokenets indhold: er tokenet udløbet (`exp` overskredet)? Er issuer (`iss`) og audience (`aud`) som forventet? etc. Hvis noget af dette fejler (f.eks. ugyldig signatur eller udløbet token), afvises anmodningen som _unauthorized_.

**Adgang eller afvisning** 
Hvis JWT er gyldig og brugeren har de nødvendige rettigheder (fx baseret på claims som roller eller tilladelser i tokenet), tillader serveren adgang til den ønskede ressource og udfører forespørgslen. Hvis tokenet er ugyldigt eller brugeren ikke er autoriseret, returnerer serveren en fejlkode (typisk HTTP 401 Unauthorized for ugyldigt token, eller 403 Forbidden hvis tokenet er gyldigt men brugeren ikke har adgang til den pågældende ressource).


Hele denne proces foregår uden, at serveren behøver at gemme sessionstilstand for brugeren – al nødvendig information til at verificere brugerens identitet og rettigheder findes i tokenet selv (deraf _self-contained_ token). 
Dette gør JWT-baseret autentifikation skalerbar og velegnet til distribuerede systemer, da enhver serverinstans kan validere et token uafhængig.

![[JWT.png]]

![[JWT SD.png]]



### Hvorfor anvendes JWT? (Fordele)
---
JWT’s popularitet skyldes en række fordele sammenlignet med traditionelle session-baserede mekanismer:

**Tilstandsløs autentifikation**
 JWT muliggør _stateless_ login-håndtering – serveren behøver ikke opbevare sessioner i hukommelse eller database for hver bruger; tokenet indeholder selv alle nødvendige data om brugeren. Dette forenkler skalering (flere servere kan verificere tokens uden fælles sessionslager).

**Kompakt og hurtigt:** 
JWT’er er designet til at være små (efter Base64URL-kodning) og kan derfor sendes effektivt i f.eks. HTTP headers. Det gør dem velegnede til brug i performancekritiske miljøer og på tværs af netværk (især relevant i API’er hvor hvert request medbringer tokenet).

**Sikkerhed og integritet** 
Fordi en JWT er signeret (med en hemmelig delt nøgle eller en privat nøgle i asymmetriske systemer), kan modtageren kontrollere tokenets integritet og autenticitet. Ingen kan ændre indholdet (claims) uden at invalidere signaturen, hvilket gør JWT _tamper-proof_.

**Teknologi-agnostisk (interoperabilitet)** 
JWT er en åben standard baseret på JSON og understøttes på tværs af mange platforme og programmeringssprog (JavaScript, Python, .NET, Java, osv.). Det gør det let at integrere JWT-baseret autentifikation i forskellige systemer og klienttyper (web, mobil, desktop).

**Indbygget udløbstid** 
En JWT kan indeholde et udløbstidspunkt (`exp` claim). Tokenet bliver ugyldigt efter en bestemt tidsperiode, hvilket reducerer risikoen ved lækkede eller stjålne tokens, da de kun kan misbruges indtil de udløber. Man kan også inkludere “issued at” (`iat`) og “not before” (`nbf`) claims for finmere kontrol med tokenets gyldighedsvindue.


Disse fordele gør JWT til et populært valg for moderne autentifikationsløsninger, især i distribuerede websystemer. JWT giver en sikker, hurtig og stateless måde at håndtere bruger-login på, uden at skulle gemme sessioner server-side.

### Typiske anvendelsesscenarier for JWT
---
JWT anvendes i dag bredt i en række sammenhænge, hvor sikker identitets- og dataudveksling er påkrævet:

**Autentifikation og autorisation i web-API’er** 
Dette er det mest almindelige anvendelsesområde. Efter en bruger logger ind, udsteder serveren et JWT _access token_. Ved alle efterfølgende API-kald fra klienten medsendes tokenet, og API’en kan afgøre om anmodningen er tilladt ud fra tokenets indhold (uden yderligere databaseopslag for session. Denne model bruges ofte i Single-Page Applications (SPA) og mobile apps, der kommunikerer med en stateless RESTful backend.

**Single Sign-On (SSO)** 
JWT er velegnet til SSO på tværs af domæner og applikationer. Fordi tokenet er kompakt og uafhængigt af oprindelsesdomænet, kan det udstedes af én autoritet (Identity Provider) og derefter accepteres af flere forskellige applikationer/domæner. Moderne SSO-løsninger benytter netop JWT på grund af dets lille overhead og nemme brug på tværs af domæner. For eksempel bruger OpenID Connect standarden JWT som **ID-token** til at repræsentere brugerens login-status på tværs af klienter.

**Sikker dataudveksling mellem tjenester** 
JWT kan også bruges som et generelt format til at udveksle pålidelige oplysninger mellem systemer. Fordi tokenet er signeret, kan modtageren verificere at afsenderen er autentisk, og at indholdet ikke er blevet ændret undervejs. Dette er nyttigt i mikroservice-arkitekturer, hvor en JWT kan indeholde brugerens rettigheder og kontekstoplysninger, som flere tjenester kan læse og respektere uden at kalde en central auth-server for hver forespørgsel.

**OAuth 2.0 adgangstokens** 
I mange OAuth2-baserede systemer (som f.eks. autorisationsservere eller Identity-as-a-Service udbydere) benyttes JWT-formatet til _access tokens_. Et OAuth access token i JWT-format bærer oplysninger om tilladelser (scopes), udsteder, udløb osv., som API’er kan validere lokalt. Det betyder, at API’et ikke behøver slå tokenet op centralt for at kontrollere gyldighed – signaturen og claims er tilstrækkelige til at verificere tokenet.

Generelt bruges JWT, når man har brug for en **stateless, pålidelig** måde at overføre identitets- eller sessionsdata mellem en udsteder og en forbruger af informationen. Hvis applikationen kræver at kunne validere en brugers identitet hurtigt og på tværs af flere komponenter uden central lagring, er JWT et oplagt valg.

### JWT i API-sikkerhed (særligt fokus)
---
I forbindelse med web-API’er udgør JWT et kernestykke i moderne sikkerhedsarkitektur. Når et API endpoint kræver JWT-baseret godkendelse, betyder det typisk: klienten skal sende et gyldigt JWT access token med hver anmodning, og API’et vil kun honorere anmodningen, hvis tokenet validerer korrekt. Hvis token mangler eller er ugyldigt, returnerer serveren en `401 Unauthorized` (eller `403 Forbidden` afhængigt af situationen), i stedet for at omdirigere brugeren til login. Dette passer godt til rene data-API’er uden brugergrænseflade. Klienten (f.eks. en single-page app eller mobilapp) har ansvaret for at autentificere brugeren via login og modtage et token – og forny tokenet når det udløber – mens API’et udelukkende har ansvar for at **autorisere** adgangen på baggrund af det medsendte token. Denne adskillelse af ansvar øger sikkerheden og forenkler arkitekturen: API’et skal ikke vide noget om login-metoder eller brugere andet end det, der står i tokenet.

Et praktisk eksempel: Forestil dig et API med endpoint `/orders`. Klienten skal hente ordrer for en bruger, så den kalder `/orders` med `Authorization: Bearer <token>`. API’et tjekker tokenet – er signaturen gyldig? Er tokenet udstedt af vores system (issuer tjek)? Er det tiltænkt vores API (audience tjek)? Er det ikke udløbet (expiry tjek)? – og derefter eventuelt hvilke rettigheder brugeren har (fx er “role” claim = admin for at se alle ordrer?). Hvis alt er i orden, returnerer API’et data; hvis ikke, afviser det. Denne mekanisme gør det nemt at skalere API’et horisontalt og integrere med forskellige klienter, da hver request bærer sin egen autentifikationsinfo. Samtidig undgår man at sende brugerfølsomme oplysninger gentagne gange; kun tokenet sendes frem og tilbage.

For at opsummere: JWT i API’er muliggør en **stateless sikkerhedskontrol** ved hver forespørgsel. Det er grunden til, at JWT er blevet standard i RESTful API beskyttelse og ofte bruges i kombination med OAuth 2.0 (hvor OAuth leverer tokens, typisk JWT, som klienten så sender til API’et).


## Praktisk i C-sharp
---

### Generering af JWT i C# (eksempel)
---
Lad os se på, hvordan man teknisk arbejder med JWT i et .NET miljø. Til at generere og validere JWT’er i C# anvendes typisk pakken **System.IdentityModel.Tokens.Jwt**, mens integration i et ASP.NET Core API sker via **Microsoft.AspNetCore.Authentication.JwtBearer** middleware.

For at **generere** et JWT i C# kan man gøre følgende:

1. **Opsæt claims:** Først defineres de oplysninger (claims) tokenet skal indeholde om brugeren eller sessionen. Dette kan være standard-claims som fx bruger-ID, brugernavn/email, udstedelsestid, udløbstid, roller m.m.
    
2. **Vælg signeringsnøgle og algoritme:** Vælg en hemmelig nøgle (for HMAC) eller et nøglepar (for RSA/ECDSA) og tilsvarende algoritme. For symmetrisk signatur (HMAC) kan nøglen være en tilfældigt genereret streng som kun serveren kender.
    
3. **Opret JWT token objekt:** Brug `JwtSecurityToken` klassen til at oprette selve tokenet ved at angive issuer, audience, claims, udløbstid osv., samt tilknytte signeringsoplysningerne.
    
4. **Seriel token til string:** Brug `JwtSecurityTokenHandler` til at serialisere token-objektet til en kompakt JWT string, som kan udleveres til klienten.
    

Nedenfor er et kodeeksempel, der illustrerer disse trin i C# (.NET):

```csharp
using System;
using System.Text;
using System.IdentityModel.Tokens.Jwt;
using System.Security.Claims;
using Microsoft.IdentityModel.Tokens;

public string GenererToken(string userId, string userEmail, string userRole)
{
    // 1. Definér claims for brugeren
    var claims = new[] 
    {
        new Claim(JwtRegisteredClaimNames.Sub, userId),           // Subjekt (typisk bruger-ID)
        new Claim(JwtRegisteredClaimNames.Email, userEmail),      // Brugers email
        new Claim(ClaimTypes.Role, userRole),                     // Brugers rolle
        new Claim(JwtRegisteredClaimNames.Iat, 
                  DateTimeOffset.UtcNow.ToUnixTimeSeconds().ToString(), 
                  ClaimValueTypes.Integer64)                     // Udstedelsestid (iat) som UNIX timestamp
    };

    // 2. Vælg en hemmelig nøgle og algoritme (HMAC SHA256 her)
    var secretKey = "min-meget-hemmelige-noegle!123";  // OBS: opbevar sikkert, og mindst 16 karakterer
    var key = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(secretKey));
    var creds = new SigningCredentials(key, SecurityAlgorithms.HmacSha256);

    // 3. Opret JWT token objekt med issuer, audience, claims og udløbstid
    var token = new JwtSecurityToken(
        issuer: "https://mit-udsteder-domæne.com",     // Udsteder af token (iss)
        audience: "https://mit-api-domæne.com",        // Tiltænkt modtager (aud)
        claims: claims,
        notBefore: DateTime.UtcNow,                    // Nbf (kan også udelades)
        expires: DateTime.UtcNow.AddHours(1),          // Expiration (exp) – token gyldigt i 1 time
        signingCredentials: creds                      // Signeringsoplysninger (nøgle + algoritme)
    );

    // 4. Serialiser token til en kompakt JWT string
    string jwtToken = new JwtSecurityTokenHandler().WriteToken(token);
    return jwtToken;
}
```


I koden her skabes et JWT med en HMAC-SHA256 signatur. Vi angiver issuer (udsteder) og audience (målgruppe) som URI’er – i en rigtig applikation vil disse være værdier, din API-løsning forventer. Vi tilføjer et sæt af claims: her bruger-id (sub), email, rolle samt `iat` (udstedelsestidspunkt). Udløbstiden sættes til 1 time frem (`AddHours(1)`). Den hemmelige nøgle er her hårdkodet for eksemplets skyld, men bør normalt komme fra konfiguration (appsettings) og have høj entropi. Vi bruger `SymmetricSecurityKey` til at repræsentere nøglematerialet og `SigningCredentials` til at binde nøgle og algoritme sammen. Til sidst genererer vi JWT-strengen ved `WriteToken`. Resultatet (`jwtToken`) er en tekststreng, fx:

```php
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...<payload>...<signature>
```

som kan udleveres til klienten ved login.

### Validering af JWT i C# (eksempel)
---
Når en klient sender en JWT med i en anmodning, skal serveren validere tokenet. I .NET bruges `JwtSecurityTokenHandler` sammen med et sæt **TokenValidationParameters** til at gøre dette. Typisk vil man lade rammeværket (JwtBearer middleware) håndtere valideringen automatisk (mere om det nedenfor), men det kan demonstreres manuelt sådan her:

```csharp
using System;
using System.IdentityModel.Tokens.Jwt;
using Microsoft.IdentityModel.Tokens;
using System.Security.Cryptography;

// Metode der validerer et JWT token og returnerer om det er gyldigt
public bool ValidateToken(string token, out ClaimsPrincipal principal)
{
    // Definér de kriterier tokenet skal opfylde:
    var validationParams = new TokenValidationParameters
    {
        ValidateIssuer = true,
        ValidIssuer = "https://mit-udsteder-domæne.com",      // skal matche issuer i token
        ValidateAudience = true,
        ValidAudience = "https://mit-api-domæne.com",         // skal matche audience i token
        ValidateIssuerSigningKey = true,
        IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(secretKey)), // samme nøgle som blev brugt til signering
        ValidateLifetime = true, // tjekker exp og nbf
        ClockSkew = TimeSpan.Zero // ingen tids-skævhed tilladt (standard er ellers ±5 min)
    };

    principal = null;
    try 
    {
        // Forsøg at validere tokenet
        var tokenHandler = new JwtSecurityTokenHandler();
        principal = tokenHandler.ValidateToken(token, validationParams, out SecurityToken validatedToken);
        // Ekstra tjek: Er det forventet signatur-algoritme?
        if (!(validatedToken is JwtSecurityToken jwt) || 
             !jwt.Header.Alg.Equals(SecurityAlgorithms.HmacSha256, StringComparison.Ordinal))
        {
            return false; // forkert algoritme eller token-format
        }
        return true; // Token er gyldigt
    } 
    catch (SecurityTokenException ex) 
    {
        // Validering fejlede (ugyldig signatur, udløbet, etc.)
        Console.WriteLine($"Token valideringsfejl: {ex.Message}");
        return false;
    }
}
```

Ovenfor opstilles valideringsparametre: vi kræver korrekt issuer og audience, vi angiver den samme signing key som blev brugt ved generering (her antaget kendt via `secretKey` variablen), og slår livstids-validering til. `ValidateToken`-metoden kaster en exception hvis token ikke er gyldigt (hvilket vi fanger). Hvis valideringen lykkes, får vi tilbage en `ClaimsPrincipal` (outputtes via `principal`), som indeholder brugerens identitet og claims fra tokenet. I eksemplet er der også illustreret et ekstra tjek på, at det modtagne tokens header faktisk bruger den forventede algoritme (HS256) – dette er god praksis for at undgå _algoritme-indsatser_, hvor nogen forsøger at sende et token signeret med en anden algoritme end din server forventer.

I praksis vil man sjældent selv kalde `ValidateToken` direkte i et API-endpoint; i stedet konfigurerer man JWT-validering som en del af ASP.NET Cores middleware pipeline, således at alle indkommende requests automatisk bliver kontrolleret for et gyldigt token, **før** de rammer din egen forretningslogik. Det er det vi kigger på nu.

### JWT i ASP.NET Core Web API (integration)
---
ASP.NET Core gør det relativt enkelt at integrere JWT-baseret autentifikation i et Web API-projekt. Man benytter den indbyggede **JwtBearer**-godkendelseshandler, som leveres af pakken `Microsoft.AspNetCore.Authentication.JwtBearer`. Denne middleware tager sig af at:

- Læse `Authorization`-headeren for indkommende HTTP-requests.
    
- Udpakke JWT-tokenet hvis tilstede, og validere dets signatur og indhold (ifølge de parametre du sætter op).
    
- Oprette en `ClaimsPrincipal` (brugeridentitet) for en gyldig token, så den kan tilgås i controller-kode, eller afvise anmodningen med 401 hvis token er manglende/ugyldig.
    

For at konfigurere dette i en ASP.NET Core applikation, tilføjer man typisk følgende i **Startup.cs** (ASP.NET Core 5 og tidligere) eller i **Program.cs** (Minimal APIs i .NET 6/7/8):

```csharp
// i ConfigureServices / før builder.Build() i Program.cs:
services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
        .AddJwtBearer(options =>
        {
            options.RequireHttpsMetadata = false;    // Kun til udvikling (tillad HTTP)
            options.SaveToken = true;                // Gem token i HttpContext (AuthenticationProperties)
            options.TokenValidationParameters = new TokenValidationParameters
            {
                ValidateIssuerSigningKey = true,
                IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(secretKey)), // samme nøgle som ved udstedelse
                ValidateIssuer = true,
                ValidIssuer = "https://mit-udsteder-domæne.com",
                ValidateAudience = true,
                ValidAudience = "https://mit-api-domæne.com",
                RequireExpirationTime = true,
                ValidateLifetime = true,
                ClockSkew = TimeSpan.Zero             // Strengt udløbstidspunkt, ingen slack
            };
        });

// ... andre service-registreringer ...

// i Configure / efter app bygges:
app.UseAuthentication();  
app.UseAuthorization();

// Map routes/endpoints:
app.MapControllers(); // for eksempel
```

Her specificerer vi, at vi bruger JWT Bearer Authentication som den **default** autentifikationsmetode. Vi angiver vores valideringsregler (samme som i det foregående afsnit): nøgle, issuer, audience, livtid osv. Det er vigtigt, at `app.UseAuthentication()` kaldes **før** `UseAuthorization()` og før definitionen af de beskyttede endpoints, så middleware’en når at fange og validere tokens på alle indkommende requests.

Når denne konfiguration er på plads, kan man beskytte sine controller-endpoints ved at tilføje attributten `[Authorize]` på de controllers eller metoder, der kræver login. ASP.NET Core vil da automatisk kræve et gyldigt JWT for at tilgå disse endpoints. Hvis en anmodning kommer uden gyldigt token, vil den blive afvist med en 401 Unauthorized, og koden i controlleren vil slet ikke blive kørt. Hvis tokenet er gyldigt, vil brugerens claims (fra JWT payload) blive tilgængelige via f.eks. `User.Identity.Name` eller `User.Claims` inde i controller-koden. Man kan desuden konfigurere rolle-baseret autorisation – f.eks. `[Authorize(Roles = "Admin")]` – hvis tokenet indeholder et `role` claim, således at kun brugere med en bestemt rolle får adgang til et givent endpoint.

Det typiske forløb i et ASP.NET Core JWT-beskyttet API er dermed:

1. **Bruger autentificeres** et sted (fx via et login-endpoint eller eksternt IdP), og der udstedes et JWT til klienten.
    
2. **Klient kalder API** og sender JWT med i headeren.
    
3. **JwtBearer middleware** snupper requestet, validerer tokenet (signatur, udløb, osv.).
    
    - Hvis validering fejler, returneres automatisk 401 Unauthorized til klienten.
        
    - Hvis validering lykkes, oprettes der en brugerprincipal (User) baseret på tokenets claims.
        
4. **API-kode autoriserer**: Controlleren/endpointet kører nu, og kan evt. lave yderligere tjek – f.eks. om brugeren har de fornødne rettigheder ift. business logic (som også kan styres via policies/roller defineret globalt).
    
5. **Response returneres**: API’et sender svar tilbage til klienten. Klienten kan på baggrund heraf foretage næste skridt, og forny tokenet når det udløber (typisk ved at ramme login/refresh-token endpoint igen).
    

Med denne opsætning håndteres de fleste detaljer af rammeværket. `Microsoft.AspNetCore.Authentication.JwtBearer` biblioteket integrerer tæt med ASP.NET Core’s autentifikations- og autorisationssystem, hvilket betyder at man kan fokusere på forretningslogikken, vel vidende at alle kald bliver filtreret for gyldig JWT først.

### Afrunding
---
JWT er et kraftfuldt værktøj i moderne webudvikling, især for API-sikkerhed. Det kombinerer et enkelt koncept – JSON-baserede _claims_ – med robust kryptografi, hvilket resulterer i et letvægts, selvbærende token, der kan rejse sikkert mellem klient og server. Ved at forstå både de konceptuelle aspekter (hvad et JWT indeholder, og hvorfor det er nyttigt) og de tekniske implementeringsdetaljer (hvordan man genererer, validerer og anvender det i f.eks. ASP.NET Core), er man godt rustet til at bygge sikre og skalerbare autentifikationsløsninger. JWT’er bruges i alt fra SPA/Mobile login flows til microservice-arkitekturer og OAuth2/OIDC – og med den pædagogiske forklaring og kodeeksemplerne her skulle det være klart, hvordan JWT fungerer, og hvordan du kan implementere det i dine egne projekter.