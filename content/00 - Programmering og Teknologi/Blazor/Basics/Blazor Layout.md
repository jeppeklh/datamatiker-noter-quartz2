> [!tldr] Definition
> Layout-komponenter giver en ensartet struktur på tværs af flere pages, for eksempel en fast header, navigationsmenu og footer. 
Ved at definere et layout kan du centralt styre den overordnede visuelle ramme for din applikation.

---

## Definition af et Layout
Et typisk layout defineres i en fil som `MainLayout.razor`:
```razor
@inherits LayoutComponentBase

<div class="sidebar">
    <!-- Indhold til sidebar, f.eks. navigation -->
</div>

<div class="main">
    @Body
</div>
```
Her bruges `@Body`-direktivet til at inkludere indholdet fra den aktuelle page, som benytter layoutet.

---

## Anvendelse af et Layout i en Page
For at anvende et layout i en page, specificeres layoutet med `@layout`-direktivet:
```razor
@page "/example"
@layout MainLayout

<h3>Example Page</h3>
<p>Dette er en side med et defineret layout.</p>
```
Dette sikrer, at siden "Example Page" bliver indrammet af `MainLayout`.

---

## Resourcer
- [Blazor Læringsobjekt (Sider, Routing, og Layout)](https://scorm.itslearning.com/data/3289/C20150/ims_import_36/scormcontent/index.html#/lessons/4pQ8P73TM5_n2DvVQakAKJ0aK-vN8yPt)
- [Blazor LinkedIn (Pages, Routing, and Layout)](https://www.linkedin.com/learning/front-end-web-development-with-dot-net/pages-routing-and-layouts-in-blazor?resume=false&u=57075649)