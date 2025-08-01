> [!tldr] Definition  
> Tags der ændrer tekstens udseende eller betydning _uden_ [[CSS]]. Fokuserer på semantik (betydning) eller visuelle ændringer via inline-elementer.

---
## Tags og deres funktioner
---
- **`<strong>`**
    - **Funktion:** Marker tekst som **vigtig** (typisk fed tekst).
    - **Attributter:** `id`, `class`, `style`, `lang`.
    - **Bemærk:** Semantisk tag – ikke kun visuel fed tekst.

- **`<em>`**
    - **Funktion:** Marker tekst som _fremhævet/emfaseret_ (typisk kursiv).
    - **Attributter:** Samme som `<strong>`.
    - **Bemærk:** Betydningsmæssig fremhævning, f.eks. sætningsbetoning.

- **`<mark>`**
    - **Funktion:** Fremhæver tekst med en markeringsfarve (som en highlighter).
    - **Attributter:** `title` (forklaring), `class` (for [[CSS]]-farve).

- **`<del>` og `<ins>`**
    - **Funktion:**
        - `<del>`: Viser ~~slettet tekst~~.
        - `<ins>`: Viser <ins>ny tilføjet tekst</ins>.
    - **Attributter:** `datetime` (dato for ændring), `cite` (kilde-URL).

- **`<code>`**
    - **Funktion:** Marker kode/funktioner (vises med `monospace`-skrift).
    - **Bemærk:** Brug `<pre>` til flere linjers kodeblokke.

- **`<small>`**
    - **Funktion:** Viser tekst i mindre skriftstørrelse (f.eks. disclaimers).
    - **Bemærk:** Semantisk "sidekommentar", ikke kun visuel lille tekst.

- **`<sup>` og `<sub>`**
    - **Funktion:**
        - `<sup>`: Ophævet tekst (f.eks. x²).
        - `<sub>`: Nedsænket tekst (f.eks. H₂O).

- **`<span>`**
    - **Funktion:** Generisk inline-container til CSS/JS-styling _uden_ semantik.
    - **Attributter:** `class`, `id`, `style`.



## Eksempel
---
```HTML
<p>  
  <strong>Advarsel:</strong> Brug <em>altid</em> sikkerhedsudstyr.<br>  
  <mark>Ny pris:</mark> <del>500 kr.</del> <ins>399 kr.</ins><br>  
  Vandstof formel: H<sub>2</sub>O. Kvadrat: 3<sup>2</sup> = 9.<br>  
  <code>console.log("Hej verden");</code>  
</p>  
```


## Vigtige regler
---
1. **Semantik før styling:** Brug `<strong>`/`<em>` i stedet for `<b>`/`<i>` medmindre det _kun_ er visuel fremhævning.
2. **Undgå forældede tags:** F.eks. `<font>` eller `<center>` – brug [[CSS]].
3. **Kombiner med CSS:** F.eks. `<span class="highlight">` til brugerdefineret styling.
4. **Nest korrekt:** Inline-tags skal altid være _inde i blok-elementer_ som `<p>` eller `<div>`.
5. **Tilgængelighed:** Skærmlæsere læser `<strong>`/`<em>` med anderledes tonehøjde.