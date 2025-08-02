
>[!tldr] Definition
>Overskrifter bruges til at definere titler og undertitler på en webside. De hjælper med at skabe hierarki og struktur for både brugere og søgemaskiner (`h1` til `h6`), hvor `h1` er den vigtigste.

---

## Tags og deres funktioner
**`<h1>` til `<h6>`**
- **Funktion:** Definerer overskriftens niveau (h1 = højeste prioritet, h6 = laveste).
- **Attributter:** `id`, `class`, `style`, `lang`, `aria-*` (til accessibility).
- **Bemærk:** Bør altid følge hierarkisk rækkefølge (f.eks. ikke hoppe fra h2 til h4).

**Typisk brug:**
- `<h1>`: Hovedtitel på siden (kun én per side til SEO).  
- `<h2>`: Underafsnit.
- `<h3>`: Underpunkt til h2-sektioner.

---

## Eksempel
```HTML
<h1>Velkommen til min blog</h1>
<h2>Seneste indlæg</h2>
<h3>Mit første rejseoplevelse</h3>
```

---

## Vigtige regler
1. Brug kun én `<h1>` per side.
2. Spring ikke niveauer over (f.eks. `<h2>` → `<h4>`).
3. Brug [[CSS]] til styling i stedet for at vælge overskrifter baseret på udseende.