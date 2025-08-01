## Bitwise Operators (bitvise operatorer)
---
Bitvise operatorer arbejder på 32-bit heltal på **bit-niveau**:

|Operator|Navn|Eksempel|
|---|---|---|
|`&`|AND|`5 & 3` → `1`|
|`|`|OR|
|`^`|XOR|`5 ^ 3` → `6`|
|`~`|NOT|`~5` → `-6`|
|`<<`|Venstreskift|`5 << 1` → `10`|
|`>>`|Højreskift|`5 >> 1` → `2`|
|`>>>`|Zero-fill højreskift|`-5 >>> 1` → `2147483645`|

### Eksempel
```js
5 & 3      // 0101 & 0011 = 0001 → 1
5 | 3      // 0101 | 0011 = 0111 → 7
```

## Logical Operators (logiske operatorer)
---
Logiske operatorer arbejder med **"truthy" og "falsy"** værdier, ikke kun booleans:

|Operator|Navn|Beskrivelse|
|---|---|---|
|`&&`|AND|Returnerer første falsy, ellers sidste truthy|
|`||`|
|`!`|NOT|Negerer sandhedsværdien|

### Eksempler
```js
0 && "Hello"        // 0     → fordi 0 er falsy
"Hello" || "World"  // "Hello" → første truthy

!true               // false
!0                  // true
```

### Short-Circuit Logic
---
Logiske operatorer evaluerer **kun** anden operand hvis nødvendigt:

```js
const name = o && o.getName(); // getName() kaldes kun hvis o er truthy
```

Anvendes også til caching:
```js
const name = cachedName || (cachedName = getName());
```