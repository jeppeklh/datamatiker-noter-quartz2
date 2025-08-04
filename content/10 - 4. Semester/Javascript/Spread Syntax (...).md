> [!tldr] Definition
> Spread-syntaks bruges til at udvide iterable elementer som arrays eller strings til individuelle elementer. 
> Den kan også anvendes til at kopiere og sammenflette arrays og objekter.

---

## Funktionskald

Spread kan bruges til at sende elementer i et array som individuelle argumenter til en funktion.

```js
function sum(x, y, z) {   
	return x + y + z; 
}  

const numbers = [1, 2, 3]; 
sum(...numbers); // 6
```

---

## Array-literals

Du kan bruge spread til at kombinere arrays eller indsætte elementer.

```js
const a = [1, 2];
const b = [3, 4];
const combined = [...a, ...b]; // [1, 2, 3, 4]
```

Array-kopi:
```js
const original = [1, 2, 3];
const copy = [...original]; // [1, 2, 3]
```

---

## Objekt-literals

Spread kan også bruges til at kopiere eller sammenflette objekter.
```js
const obj1 = { a: 1, b: 2 };
const obj2 = { b: 3, c: 4 };
const merged = { ...obj1, ...obj2 }; 
// { a: 1, b: 3, c: 4 }
```

---
## Bemærkninger

- Spread laver kun en **shallow copy**. Indlejrede objekter bliver ikke dybdekopieret.
    
- Kun **iterable** værdier (f.eks. arrays og strings) kan bruges med spread i arrays og funktionskald.
    
- I objekter overskriver efterfølgende egenskaber de tidligere, hvis nøglerne er ens.


---
## Resourcer
- [Spread Syntax Dokumentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)