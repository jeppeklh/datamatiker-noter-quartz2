> [!tldr] Definition  
> Bruges til at opdele tekst i logiske afsnit (`<p>`) og indsætte enkeltstående linjeskift (`<br>`). Mens `<p>` skaber et nyt tekstblok-element, er `<br>` kun til linjehop _inden for_ samme afsnit.

---

## Tags og deres funktioner
- **`<p>`**
    - **Funktion:** Definere et tekstafsnit (blok-element med automatisk margen ovenfor/nedenunder).
    - **Attributter:** `id`, `class`, `style`, `lang`, `aria-*`.
    - **Bemærk:** Browser tilføjer automatisk luft mellem `<p>`-elementer.

- **`<br>`**
    - **Funktion:** Tvungent linjeskift (inline-element _uden_ ny margen).
    - **Attributter:** `id`, `class`, `style`, `title`.
    - **Bemærk:** Er et _tomt element_ (skrives som `<br>` eller `<br/>` i XHTML).
        
---

## Eksempel
```HTML
<p>Dette er et afsnit med en lang tekst.<br>
Her fortsætter teksten på en ny linje i SAMME afsnit.</p>

<p>Dette er et nyt afsnit med egen margen.</p>
```

---

## Vigtige regler
1. **Undgå "lazy line breaks":** Brug ikke `<br>` til at lave store mellemrum – brug [[CSS]] `margin/padding` i stedet.
2. **Nest korrekt:** `<br>` skal ALTID være inde i et `<p>`/`<span>`/andet tekst-container-element.
3. **Semantisk brug:** `<p>` er til sammenhængende tekst, ikke til layout-ting som f.eks. billedtekster (brug `<figure>`+`<figcaption>`).