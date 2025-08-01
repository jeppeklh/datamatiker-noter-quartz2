> [!tldr] Definition
Genanvendelige dele af UI bygget med JavaScript og JSX.  
De gør det muligt at indkapsle markup, style og logik ind i selvstændige elementer.
## Key Characteristics
---
- En React component er bare en **JavaScript function**.
    
- Funktionen **skal starte med stort bogstav**.
    
- Components returnerer **JSX** – syntaks der ligner HTML i JavaScript

### Example: basic component
---
```jsx
export default function Profile() {
  return (
    <img 
      src="https://i.imgur.com/MK3eW3As.jpg" 
      alt="Katherine Johnson" 
    />
  );
}
```


## Using Components
---
Du kan **neste** components inden i hinanden, ligesom HTML-elementer.

```jsx
function Profile() {
  return (
    <img 
      src="https://i.imgur.com/MK3eW3As.jpg" 
      alt="Katherine Johnson" 
    />
  );
}

export default function Gallery() {
  return (
    <section>
      <h1>Amazing scientists</h1>
      <Profile />
      <Profile />
      <Profile />
    </section>
  );
}

```

## Best Practices
---
- Definér altid components på **top level**, ikke inde i andre components.
    
- Brug **JSX** korrekt:
    - Wrap multilinjede JSX i parenteser efter `return`.
    - Brug **self-closing tags** som `<img />` hvis der ikke er nogen children.

- Component-navne skal starte med **store bogstaver**, så React kan skelne dem fra HTML-tags.

## Composition
---
React opfordrer til at bygge UIs ved at bruge components**:
```jsx
<PageLayout>
  <NavigationHeader>
    <SearchBar />
    <Link to="/docs">Docs</Link>
  </NavigationHeader>
  <Sidebar />
  <PageContent>
    <TableOfContents />
    <DocumentationText />
  </PageContent>
</PageLayout>
```

## Resourcer
---
- [FSO](https://fullstackopen.com/en/part1/introduction_to_react)
- [Components documentation](https://react.dev/learn/your-first-component)