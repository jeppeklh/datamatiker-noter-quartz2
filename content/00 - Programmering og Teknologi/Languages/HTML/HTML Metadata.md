>[!tldr] Definition
>HTML-metadata giver information om dokumentet, som ikke vises direkte på siden. Metadata placeres i `<head>`-sektionen og bruges af browsere, søgemaskiner og andre tjenester.

---

## `<head>`-elementet
Containeren for alle metadata-tags, der beskriver dokumentet. Typiske elementer inkluderer:
  - `<meta>`
  - `<title>`
  - `<link>`
  - `<script>`

---

## `<title>` Tag
Angiver sidens titel, som vises i browsertabben og i søgeresultater.

```html
<title>Min Webside</title>
```

---

## `<meta>` Tags
### Karakterkodning
Specificerer den tegnsætning, der anvendes i dokumentet, så f.eks. æ, ø og å vises korrekt.
```HTML
<meta charset="UTF-8">
```
### Viewport
Sørger for, at siden skalerer korrekt på mobile enheder og tablets.
```HTML
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### Beskrivelse
Giver en kort beskrivelse af siden, som ofte bruges af søgemaskiner til at vise en preview.
```HTML
<meta name="description" content="En kort beskrivelse af siden">
```

### Nøgleord
Angiver relevante søgeord for siden (bruges mindre i moderne SEO).
```HTML
<meta name="keywords" content="HTML, Metadata, Webudvikling">
```

### Forfatter
Angiver forfatteren af siden.
```HTML
<meta name="author" content="Dit Navn">
```

### Andre Metadata
Sikrer, at Internet Explorer bruger den nyeste rendering engine.
```HTML
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

---

## `<link>` Tag
Forbinder dokumentet med eksterne ressourcer som f.eks. [[CSS]]-filer, favicons eller skrifttyper.
```HTML
<link rel="stylesheet" href="styles.css">
```

---

## Eksempel på et komplet `<head>`-afsnit
```HTML
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="En kort beskrivelse af siden">
    <meta name="keywords" content="HTML, Metadata, Webudvikling">
    <meta name="author" content="Dit Navn">
    <title>Min Webside</title>
    <link rel="stylesheet" href="styles.css">
</head>
```