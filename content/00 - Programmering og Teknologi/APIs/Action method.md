> [!tldr] Definition
En **Action Method** er en metode i en ASP.NET MVC-controller, der håndterer [[REST API#**HTTP-metoder**|HTTP-metoder]].

## Karakteristika
---
- Defineres i en controller (`Controller`-klasse).
- Returnerer et **ActionResult** eller en anden datatype.
- Kan håndtere forskellige [[REST API#**HTTP-metoder**|HTTP-metoder]] (`GET`, `POST`, `PUT`, `DELETE` osv.).

## Eksempel
---

```csharp
public class HomeController : Controller
{
    // Håndterer en HTTP POST-request
    [HttpPost]
    public IActionResult SubmitForm(FormModel model)
    {
        if (ModelState.IsValid)
        {
            return RedirectToAction("Success");
        }
        return View(model);
    }
}
