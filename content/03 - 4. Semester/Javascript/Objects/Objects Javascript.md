> [!note] note
> Der findes flere måder at definere objekter på i JavaScript. En meget almindelig metode er at bruge **object literals**, hvor man angiver properties inden for tuborgklammer

```js
const object1 = {
  name: 'Arto Hellas',
  age: 35,
  education: 'PhD',
}

const object2 = {
  name: 'Full Stack web application development',
  level: 'intermediate studies',
  size: 5,
}

const object3 = {
  name: {
    first: 'Dan',
    last: 'Abramov',
  },
  grades: [2, 3, 5, 3],
  department: 'Stanford University',
}
```
Værdierne i et objekt kan være af enhver datatype, f.eks. int, sting, arrays, objekter osv.

### Adgang til properties
Properties i et objekt tilgås enten med **dot notation** eller med **bracket notation**:
```js
console.log(object1.name)         // Udskriver: Arto Hellas
const fieldName = 'age'
console.log(object1[fieldName])   // Udskriver: 35
```

---
### Tilføjelse af egenskaber

Du kan tilføje nye properties til et objekt løbende, med enten punkt- eller bracket-notation:
```js
object1.address = 'Helsinki'
object1['secret number'] = 12341
```
Den sidste tilføjelse skal bruge brackets, fordi `"secret number"` indeholder et mellemrum, og det er ikke en gyldig propertynavn med dot notation.

---
### Objekt shorthand

Når navnet på en variabel og navnet på en property er det samme, kan du forkorte din kode ved at bruge **shorthand-syntaks**:

```js
const name = 'Leevi'
const age = 0

const person = { name, age } // Samme som: { name: name, age: age }
```

Det skaber et objekt som
```js
{ name: 'Leevi', age: 0 }
```


