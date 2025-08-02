> [!tldr] Definition  
> HTML-links (hyperlinks) bruges til at forbinde websider eller ressourcer. Det primære tag er `<a>`, der definerer et link via attributten `href`.

---

## Tags og deres funktioner
- **`<a>`**
    - **Funktion:** Opretter et klikbart link til en URL, fil, e-mail eller sidefragment (f.eks. "#kontakt").
    - **Attributter:**
        - `href`: Angiver destinations-URL (påkrævet).
        - `target`: Styrer, hvor linket åbnes (f.eks. `_blank` for ny fane).
        - `rel`: Definerer forholdet mellem dokumenter (f.eks. `nofollow` til SEO eller `noopener` for sikkerhed).
        - `download`: Tvinger fil-download i stedet for visning (f.eks. `download="fil.pdf"`).
        - `title`: Tooltip-tekst ved hover (tilgængelighed).
    - **Bemærk:** Indholdet af `<a>`-tagget er den synlige linktekst (anchor text).

---

## Eksempler
```HTML
<!-- Internt link -->  
<a href="/om-os.html">Læs mere om os</a>  

<!-- Eksternt link med sikkerhedsattributter -->  
<a href="https://eksempel.dk" target="_blank" rel="noopener noreferrer">Besøg eksempel.dk</a>  

<!-- E-mail-link -->  
<a href="mailto:kontakt@firma.dk">Send os en e-mail</a>  

<!-- Link til sidefragment (ankertag) -->  
<a href="#kontaktoplysninger">Hop til kontakt</a>  
```



## Vigtige regler
---
1. **Brug beskrivende anchor text:** Undgå "Klik her" – skriv i stedet "Læs vores guide".
2. **Eksterne links:** Brug altid `rel="noopener"` eller `rel="noreferrer"` med `target="_blank"` for at forhindre sikkerhedshuller.
3. **Tilgængelighed:**
    - Links skal kunne navigeres med tastatur.
    - Brug `title`-attribut til ekstra kontekst (f.eks. "PDF, 2 MB").
4. **SEO:** Links med `rel="nofollow"` fortæller søgemaskiner ikke skal følge linket (f.eks. brugerkommentarer).
5. **Relative vs. absolutte URLs:**
    - Relative (`/blog/2024`): Til interne links på samme domæne.
    - Absolutte (`https://domæne.dk/blog`): Til eksterne ressourcer.

## Avanceret brug
---
- **Telefonlinks:** `<a href="tel:+4512345678">Ring til os</a>`
- **Deep links:** Link til specifikke app-funktioner (f.eks. `whatsapp://send?text=Hej`).
- **Hash-links:** Spring til element med `id="kontakt"` via `<a href="#kontakt">`.