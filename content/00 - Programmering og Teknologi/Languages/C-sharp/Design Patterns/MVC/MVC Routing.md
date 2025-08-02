> [!tldr] Definition
> Routing kortlægger URL'er til specifikke controllers og actions. Altså hvilken URL hører til hvilket Endpoint

- Når en bruger indtaster en URL, bestemmer routing-mekanismen hvilken controller og action, der skal håndtere anmodningen.
- Eksempel på en standardrute:
```csharp
routes.MapRoute(
    name: "Default",
    url: "{controller}/{action}/{id}",
    defaults: new { controller = "Home", action = "Index", id = UrlParameter.Optional }
);
```

>[!example] Eksempel
>- URL: `http://example.com/Books/Details/1`
>	- **Books** → `BooksController`
>	- **Details** → `Details`-action
>	- **1** → Parameteren `id`

- **Fordele ved routing**:
    - Fleksibilitet: Mulighed for brugerdefinerede, SEO-venlige URL-mønstre.
    - Adskillelse af bekymringer: URL-strukturen adskilles fra controller-logikken.
    - Parameterhåndtering: Gør det nemt at sende parametre til controllers.

---

## Resourser
- [MVC Læringsobjekt (Routing)](https://scorm.itslearning.com/data/3289/C20150/ims_import_31/scormcontent/index.html#/lessons/XWb04QK9uDQN4TH0Aft8LTNLvo-s9y9B)