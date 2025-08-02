> [!tldr] Definition  
> Navigation i HTML struktureres med semantiske tags som `<nav>` og lister (`<ul>`/`<ol>`) for at skabe menuer eller link-samlinger. Formålet er at gøre det nemt for brugere og søgemaskiner at navigere mellem sider/sektioner.

---

## Tags og deres funktioner
- **`<nav>`**
    - **Funktion:** Marker en sektion med navigationslinks (f.eks. hovedmenu, breadcrumbs).
    - **Attributter:** `id`, `class`, `aria-label` (tilgængelighedsbeskrivelse).
    - **Bemærk:** Ikke alle link-grupper skal i `<nav>` – kun primær navigation.

- **`<ul>`/`<ol>` + `<li>`** (Se [[HTML Lister]])
    - **Funktion:** Opretter lister til menu-items (typisk `<ul>` for unummererede menuer).
    - **Attributter:** `class` (f.eks. `class="menu"`), `role` (f.eks. `role="navigation"`).

- **`<a>` (i kombination)**
    - **Funktion:** Links i menuen peger på sider/sektioner (se [[HTML Links]])

---

## Eksempler
### Simpel navbar:
```HTML
<nav aria-label="Hovedmenu">  
  <ul>  
    <li><a href="/">Hjem</a></li>  
    <li><a href="/produkter">Produkter</a></li>  
    <li><a href="/kontakt">Kontakt</a></li>  
  </ul>  
</nav>  
```
### Dropdown-menu (kun HTML-struktur):
```HTML
<nav>  
  <ul>  
    <li><a href="/webudvikling">Webudvikling</a>  
      <ul>  
        <li><a href="/html">HTML</a></li>  
        <li><a href="/css">CSS</a></li>  
      </ul>  
    </li>  
  </ul>  
</nav>  
```

---

## Vigtige regler
1. **Semantisk korrekt:** Brug altid `<nav>` + lister – ikke `<div>`-spaghetti.
2. **Tilgængelighed:**
    - Tilføj `aria-label` til `<nav>` hvis der er flere navigationssektioner.
    - Brug tastaturvenlige menuer (f.eks. fokus på `<a>` med `tabindex`).
3. **Breadcrumbs:** Brug `<nav>` med `aria-label="Brødkrummesti"` og separatorer (f.eks. `→`).
4. **Undgå for mange niveauer:** Dropdowns med mere end 2 lag kan være uoverskuelige.
5. **SEO:** Links i `<nav>` bør pege på vigtige sider (undgå overoptimering).

---

## Avanceret brug
- **Sprogskift:** Brug `<nav>` med `hreflang`-links for international navigation.
- **Paginering:** Navigation mellem sider i en artikel:
```HTML
 <nav aria-label="Artikel navigation">  
  <a href="/side1">Forrige</a>  
  <a href="/side3">Næste</a>  
</nav>  
```


---

## Fejl at undgå
**Dårligt:**
```HTML
<div>  
  <div><a href="/">Hjem</a></div>  
  <div><a href="/om">Om os</a></div>  
</div>  
```

**Korrekt:**
```HTML
<nav>  
  <ul>  
    <li><a href="/">Hjem</a></li>  
    <li><a href="/om">Om os</a></li>  
  </ul>  
</nav>  
```