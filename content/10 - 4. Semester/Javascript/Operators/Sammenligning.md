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

## Anbefaling
---
Brug altid `===` og `!==` for at undgå utilsigtede fejl med typekonvertering.