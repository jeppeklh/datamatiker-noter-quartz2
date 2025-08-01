> [!tldr] Definition  
> Lister bruges til at gruppere relateret indhold i punktform. HTML understøtter **uordnede lister** (`<ul>`), **ordnede lister** (`<ol>`), og **definitionslister** (`<dl>`).

---

## Tags og deres funktioner
---
### **Uordnede lister**
---
- **`<ul>`**
    - **Funktion:** Opretter en liste med punkter (typisk prikker eller andre ikoner).
    - **Attributter:** `class`, `id`, `aria-label` (tilgængelighed).
    - **Bemærk:** Brug til gruppering uden rækkefølge (f.eks. navigation, ingredienser).

- **`<li>`**
    - **Funktion:** Marker et enkelt listepunkt i både `<ul>` og `<ol>`.
    - **Attributter:** `value` (kun i `<ol>` for at tilsidesætte nummerering).


### **Ordnede lister**
---
- **`<ol>`**
    - **Funktion:** Opretter en nummereret liste (tal, bogstaver, romertal).
    - **Attributter:**
        - `type`: Angiver nummereringstype (`1`, `A`, `a`, `I`, `i`).
        - `start`: Starter nummereringen fra en specifik værdi (f.eks. `start="3"`).
        - `reversed`: Nummerer baglæns (f.eks. `reversed`).


### **Definitionslister**
---
- **`<dl>`**
    - **Funktion:** Opretter en liste af termer og deres beskrivelser (f.eks. ordbogsartikler).

- **`<dt>`**
    - **Funktion:** Definerer en term (f.eks. et ord).

- **`<dd>`**
    - **Funktion:** Beskriver termen fra `<dt>`.



## Eksempler
---
### Uordnet liste:
```HTML
<ul>  
  <li>Kaffe</li>  
  <li>Te</li>  
  <li>Mælk</li>  
</ul>  
```
### Ordnet liste med romertal:
```HTML
<ol type="I" start="5">  
  <li>Første punkt</li>  
  <li>Andet punkt</li>  
</ol>  
```
### Definitionsliste:
```HTML
<dl>  
  <dt>HTML</dt>  
  <dd>HyperText Markup Language – brugs til websidestruktur.</dd>  
  <dt>CSS</dt>  
  <dd>Cascading Style Sheets – brugs til styling.</dd>  
</dl>  
```
### Nestede lister:
```HTML
<ul>  
  <li>Frugt  
    <ul>  
      <li>Æble</li>  
      <li>Banan</li>  
    </ul>  
  </li>  
</ul>  
```


## Vigtige regler
---
1. **Semantisk brug:**
    - Brug `<ul>` til menuer eller punkter uden rækkefølge.
    - Brug `<ol>` til trin-for-trin-guides eller ranglister.

2. **Tilgængelighed:**
    - Undgå at bruge lister _udelukkende_ til layout (f.eks. knapper arrangeret som `<li>`).
    - Brug `aria-label` eller `aria-labelledby` til komplekse lister.

3. **Styling:**
    - Ændr listemærker med [[CSS]] (`list-style-type: square;`), ikke HTML-attributter som `type`.

4. **SEO:** Lister med nøgleord i `<li>` kan forbedre læsbarheden for søgemaskiner.



