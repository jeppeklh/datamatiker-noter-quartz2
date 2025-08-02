
>[!tldr] Definition
>Et HTML-dokument starter med en grundlæggende struktur, som angiver dokumenttypen og dets hovedsektioner.

---
```html
<!DOCTYPE html> 
<html lang="da"> 
<head> 
	<meta charset="UTF-8"> 
	<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
	<title>Min Webside</title> 
</head> 
<body> 
	<h1>Velkommen til min webside</h1>
	<p>Dette er en simpel HTML-struktur.</p> 
</body> 
</html>
```

---

## Forklaring af de vigtigste tags
`<!DOCTYPE html>`
- Angiver, at dokumentet er HTML5.

`<html lang="da">`
- Rod-elementet i HTML, med angivelse af sprog (`lang="da"` for dansk).
 
 `<head>`
- Indeholder metadata om dokumentet, f.eks. tegnsætning, viewport og titel.
 
 `<meta charset="UTF-8">`
- Sikrer, at tegn som æ, ø og å vises korrekt.

`<title>`
- Bestemmer sidens titel (vises i browsertabben).

`<body>`
- Indeholder alt synligt indhold på siden.

---

##  Ekstra tips
- HTML er **ikke casesensitive**, men tags skrives normalt med små bogstaver.
- **Indrykning** gør koden lettere at læse.
- **Kommentarer** kan skrives med `<!-- Kommentar her -->`.