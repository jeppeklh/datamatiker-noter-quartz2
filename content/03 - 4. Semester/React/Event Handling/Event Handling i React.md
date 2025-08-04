> [!tldr] Definition
> I React skal event handlers være **funktioner** — enten direkte eller som reference til en funktion.

---

## Korrekt brug

Du må **ikke** bruge værdier eller funktioner, der bliver kaldt med det samme. Brug i stedet en funktion **reference** eller en **arrow function**:
```js
<button onClick={() => setValue(0)}>Reset</button>
```

Eller med en navngiven funktion:
```js
const handleClick = () => {
  console.log("clicked");
  setValue(0);
};

<button onClick={handleClick}>Reset</button>
```


---

## Forkert brug (eksempler)

**Disse virker ikke:**
```js
<button onClick={value + 1}>Fejl</button>           // returnerer tal, ikke en funktion
<button onClick={setValue(0)}>Fejl</button>         // kalder funktionen med det samme
<button onClick="reset()">Fejl</button>             // string, ikke en funktion
<button onClick={value = 0}>Fejl</button>           // muterer state direkte
<button onClick={console.log('klik')}>Fejl</button> // kalder funktionen under render

```

---

> [!note] Anbefaling
> - Brug `() => setValue(...)` eller en navngiven funktion som `handleClick`
>- Undgå at skrive funktion **kald** direkte i `onClick`

---

## Eksempel med funktionel komponent

```js
const App = () => {
  const [value, setValue] = useState(10);

  const handleClick = () => {
    console.log("clicked");
    setValue(0);
  };

  return (
    <div>
      {value}
      <button onClick={handleClick}>Reset</button>
    </div>
  );
};
```