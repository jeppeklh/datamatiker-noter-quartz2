> [!tldr] Definition
> **Destructuring** er en praktisk måde at udtrække værdier fra arrays eller properties fra objekter til separate variabler.

---

## Array Destructuring
```js
const numbers = [1, 2, 3];
const [a, b] = numbers;
console.log(a); // 1
console.log(b); // 2
```

#### Skipping items
```js
const [, , third] = numbers;
console.log(third); // 3
```

#### Default values
```js
const [x = 10, y = 20] = [];
console.log(x, y); // 10 20
```

#### Rest Pattern
Rest-mønsteret opsamler de resterende elementer eller egenskaber i et nyt array eller objekt.
```js
const [first, ...rest] = [1, 2, 3, 4];
console.log(rest); // [2, 3, 4]

const { a, ...others } = { a: 1, b: 2, c: 3 };
console.log(others); // { b: 2, c: 3 }
```

---

## Object Destructuring
```js
const user = { name: "Alice", age: 25 };
const { name, age } = user;
console.log(name); // Alice
console.log(age); // 25
```

#### Renaming
```js
const { name: userName } = user;
console.log(userName); // Alice
```

#### Default values
```js
const { role = "guest" } = user;
console.log(role); // guest
```

---

## Nested Destructuring
```js
const person = {
  name: "Bob",
  address: { city: "NY", zip: "10001" }
};
const { address: { city } } = person;
console.log(city); // NY
```

---

## Function Parameters
```js
function greet({ name }) {
  console.log(`Hello, ${name}`);
}
greet({ name: "Charlie" }); // Hello, Charlie
```

---

## Resourcer
- [Destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring)