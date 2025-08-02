> [!tldr] Definition
> Autentifikation beskytter applikationen ved at sikre, at kun autoriserede brugere har adgang til bestemte funktioner og data. Det er essentielt for at opretholde sikkerheden og integriteten af applikationen og dens data. 

Blazor understøtter forskellige autentifikationsmetoder, herunder:
- **Individuelle konti** (Identity med Entity Framework)
- **Azure Active Directory (AAD)**
- **Eksterne logins** (Google, Facebook, Twitter osv.)
- **JWT (JSON Web Tokens)**
- **API-baseret autentifikation** via IdentityServer eller andre OAuth-udbydere

---

## Opsætning af autentifikation i Blazor
### 1. Opret et Blazor-projekt med autentifikation
Når du opretter et nyt Blazor-projekt, kan du vælge at inkludere autentifikation. I **Visual Studio** kan du:
- Vælge **"Individual Accounts"** under autentifikationsindstillingerne for at bruge **ASP.NET Core Identity**.
- Alternativt vælge **"Microsoft Identity Platform"** for Azure AD-integration.

---

### 2. Konfiguration af autentifikation i Program.cs
I nyere Blazor-projekter (Blazor Server) kan autentifikation konfigureres direkte i **Program.cs**:

```csharp
var builder = WebApplication.CreateBuilder(args);

// Tilføj databasekontekst
builder.Services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));

// Tilføj ASP.NET Core Identity
builder.Services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
    .AddEntityFrameworkStores<ApplicationDbContext>();

// Tilføj Blazor og autentifikationstjenester
builder.Services.AddRazorPages();
builder.Services.AddServerSideBlazor();
builder.Services.AddScoped<AuthenticationStateProvider, RevalidatingIdentityAuthenticationStateProvider<IdentityUser>>();

var app = builder.Build();

if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}

app.UseHttpsRedirection();
app.UseStaticFiles();

app.UseRouting();

app.UseAuthentication();
app.UseAuthorization();

app.MapBlazorHub();
app.MapFallbackToPage("/_Host");

app.Run();
```

---

### 3. Beskyt komponenter med `AuthorizeView`
Blazor har en indbygget komponent, **`AuthorizeView`**, som gør det nemt at vise indhold baseret på brugerens autentifikationsstatus.
```razor
<AuthorizeView>
    <Authorized>
        <h3>Welcome, @context.User.Identity.Name!</h3>
        <p>You can see this content because you are authenticated.</p>
    </Authorized>
    <NotAuthorized>
        <h3>Please log in to see this content.</h3>
    </NotAuthorized>
</AuthorizeView>
```
- **Hvis brugeren er logget ind**, vises velkomstbeskeden.
- **Hvis brugeren ikke er logget ind**, opfordres de til at logge ind.

---

### 4. Beskyt sider og komponenter med `[Authorize]`
Du kan også beskytte hele **sider** eller **komponenter** ved hjælp af `[Authorize]`-attributten.

#### **Eksempel**: Beskyttelse af en Razor-komponent
```razor
@page "/protected"
@attribute [Authorize]

<h3>Du skal være logget ind for at se denne side</h3>
<p>Kun autoriserede brugere har adgang.</p>
```
Hvis en uautoriseret bruger forsøger at tilgå denne side, vil de blive omdirigeret til login-siden.

---

### 5. Rollebaseret adgangskontrol
Hvis du vil begrænse adgang baseret på **roller**, kan du udvide `[Authorize]`-attributten:
```razor
@attribute [Authorize(Roles = "Admin")]
```
Kun brugere med **"Admin"**-rollen kan nu få adgang til denne komponent.

Tilsvarende kan du bruge **AuthorizeView** til at vise indhold baseret på brugerens rolle:
```razor
<AuthorizeView Roles="Admin">
    <Authorized>
        <h3>Admin Panel</h3>
        <p>Kun administratorer kan se dette.</p>
    </Authorized>
</AuthorizeView>
```

---

## 6. Tilpasning af login og logout
### Login-knap

Brugere kan logge ind ved at navigere til **`/Identity/Account/Login`** i en Blazor Server-app med ASP.NET Identity.

Du kan tilføje en login-knap i din navigation:
```razor
<AuthorizeView>
    <Authorized>
        <a href="Identity/Account/Manage">Profil</a> |
        <a href="Identity/Account/Logout">Log ud</a>
    </Authorized>
    <NotAuthorized>
        <a href="Identity/Account/Login">Log ind</a>
    </NotAuthorized>
</AuthorizeView>
```

---

## 7. API-baseret autentifikation med JWT
Hvis din Blazor-app kommunikerer med et **eksternt API**, kan JWT bruges til autentifikation.

I **Program.cs**, konfigurer JWT-godkendelse:
```csharp
builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddJwtBearer(options =>
    {
        options.Authority = "https://your-auth-server.com";
        options.Audience = "your-api";
    });
```
Derefter kan du beskytte dine API-kald ved at sende en **Authorization**-header med tokenet.

---

## Konklusion
Blazor har stærk understøttelse af autentifikation via ASP.NET Core Identity, Azure AD, JWT og eksterne login-udbydere. Du kan nemt beskytte komponenter og sider med **AuthorizeView** og `[Authorize]`-attributten, samt implementere rollebaseret adgangskontrol.

**Hovedpunkter:**

- Brug **AuthorizeView** til at vise indhold baseret på login-status.
- Beskyt komponenter og sider med `[Authorize]`.
- Implementér **rollebaseret adgang** med `[Authorize(Roles = "Admin")]`.
- Understøtter både **individuelle konti**, **OAuth/JWT**, og **Azure AD**.
- Brug `Identity/Account/Login` og `Identity/Account/Logout` til login/logud i Blazor Server.

---

## Resourcer
- [Blazor WebAssembly Læringsobjekt (Autentifikation)](https://scorm.itslearning.com/data/3289/C20150/ims_import_38/scormcontent/index.html#/lessons/BteImlY66O1cDAtgfjL-ZesFTMHQvpiu)
- [Blazor WebAssembly LinkedIn Kursus (Authentication)](https://www.linkedin.com/learning/blazor-webassembly-foundational-skills/authentication-with-individual-accounts?resume=false&u=57075649)