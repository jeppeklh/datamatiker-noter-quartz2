> [!tldr] Definition
I JavaScript bruges `==` og `!=` til **sammenligning med typekonvertering**, mens `===` og `!==` sammenligner **uden** typekonvertering (streng sammenligning).

## Kort forklaret
---

|Operator|Betydning|Typekonvertering?|
|---|---|---|
|`==`|Løs lighed|Ja|
|`===`|Streng lighed|Nej|
|`!=`|Løs ulighed|Ja|
|`!==`|Streng ulighed|Nej|

## Eksempler
---
```js
// == vs ===
'5' == 5       // true  → fordi '5' konverteres til tal
'5' === 5      // false → fordi typerne er forskellige

// != vs !==
null != undefined  // false → de anses som "lige" ved løs sammenligning
null !== undefined // true  → fordi typerne er forskellige

0 == false    // true
0 === false   // false

'' == false   // true
'' === false  // false
```


---
## Object.is()
> [!tldr] Definition
> `Object.is()` sammenligner to værdier **uden typekonvertering**, ligesom `===`, men adskiller sig i enkelte specialtilfælde:

#### Vigtige forskelle fra `===`

```js
Object.is(NaN, NaN);   // true   → NaN er lig med sig selv
Object.is(+0, -0);     // false  → adskiller +0 og -0
Object.is(5, 5);       // true
Object.is('5', 5);     // false
```

>[!info] Bemærk
>Bruges sjældent i praksis, men nyttig i særlige situationer med præcis værdisammenligning.


> [!tip] Anbefaling
> - Brug altid `===` og `!==` for at undgå utilsigtede fejl med typekonvertering.
> - Brug kun `==` hvis du **bevidst** ønsker typekonvertering.  
> - `Object.is()` kan bruges til specialtilfælde som `NaN` og `+0/-0`.