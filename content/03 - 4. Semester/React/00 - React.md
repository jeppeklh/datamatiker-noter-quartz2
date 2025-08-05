> [!tldr] Definition
> React er et **JavaScript-bibliotek til opbygning af brugergrænseflader**, typisk til **single-page applications (SPA)**. 
> 
> Det gør det muligt at opbygge UI’er som en samling af **genbrugelige komponenter**, der opdateres effektivt, når data ændres.

## Nøglekoncepter

- **Komponentbaseret**: UI bygges op af selvstændige, isolerede komponenter.
    
- **Deklarativ**: Du beskriver, hvordan UI’et _skal se ud_ baseret på state.
    
- **Unidirectional Data Flow**: Data flyder fra forældrekomponenter til børn via `props`.
    
- **Virtual DOM**: React opdaterer kun det, der er nødvendigt i DOM’en for at øge performance.

---
## Eksempel på en komponent

```jsx
const Welcome = ({ name }) => {
  return <h1>Hej, {name}!</h1>;
};
```

React anvendes typisk sammen med værktøjer som Vite, Webpack eller Next.js, og integreres ofte med [[Hooks|hooks]], routing og [[useState Hook|state management]].