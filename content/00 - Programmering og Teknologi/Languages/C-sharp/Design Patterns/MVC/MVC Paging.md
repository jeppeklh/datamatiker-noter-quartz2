Når man arbejder med store datasæt, kan paging og [[MVC Sorting|sorting]] være essentielle funktioner.

## Paging (Paginering)
---
**Formål**: Opdele data i mindre sider for bedre overskuelighed og performance.

**Controller Eksempel**:
```csharp
public ActionResult Index(int page = 1, int pageSize = 10)
{
    var data = db.Items
                 .OrderBy(i => i.Id)
                 .Skip((page - 1) * pageSize)
                 .Take(pageSize)
                 .ToList();
    return View(data);
}
```

**View Eksempel**:
```HTML
@model IEnumerable<Item>
<table>
    <tr>
        <th>Id</th>
        <th>Name</th>
    </tr>
    @foreach (var item in Model)
    {
        <tr>
            <td>@item.Id</td>
            <td>@item.Name</td>
        </tr>
    }
</table>
<div>
    @for (int i = 1; i <= ViewBag.TotalPages; i++)
    {
        <a href="@Url.Action("Index", new { page = i })">@i</a>
    }
</div>
```

## Resourser
---
- [MVC Læringsobjekt (Paging og Sorting)](https://scorm.itslearning.com/data/3289/C20150/ims_import_31/scormcontent/index.html#/lessons/K6U2oV-9AY4HHEVcvluwKsn_gwPwaZtL)