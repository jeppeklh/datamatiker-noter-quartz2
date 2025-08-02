> [!note]
> Når man arbejder med store datasæt, kan [[MVC Paging|paging]] og sorting være essentielle funktioner.

**Formål**: Arrangere data i en bestemt rækkefølge (f.eks. alfabetisk, numerisk).

**Controller Eksempel**:
```csharp
public ActionResult Index(string sortOrder)
{
    ViewBag.NameSortParm = String.IsNullOrEmpty(sortOrder) ? "name_desc" : "";
    var items = from i in db.Items select i;
    switch (sortOrder)
    {
        case "name_desc":
            items = items.OrderByDescending(i => i.Name);
            break;
        default:
            items = items.OrderBy(i => i.Name);
            break;
    }
    return View(items.ToList());
}
```

---

## Resourser
- [MVC Læringsobjekt (Paging og Sorting)](https://scorm.itslearning.com/data/3289/C20150/ims_import_31/scormcontent/index.html#/lessons/K6U2oV-9AY4HHEVcvluwKsn_gwPwaZtL)