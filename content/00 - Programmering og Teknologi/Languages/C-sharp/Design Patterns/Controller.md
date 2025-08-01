tags: #C-sharp #Programmering #DesignPattern #Controller

## Definition 
---
A [[Design Patterns Overview|design pattern]] that focuses on managing the flow of the application.

Responsible for interpreting user input and invoking appropriate actions
Intermediary between the UI and the logic.


## Example
---
```csharp
// Model class
public class Model
{
    private List<string> data;
    public Model()
    {
        data = new List<string>();
    }
    public void AddData(string item)
    {
        data.Add(item);
    }
    public List<string> GetData()
    {
        return data;
    }
}
````

```csharp
// View class
public class View
{
    public void ShowData(List<string> data)
    {
        Console.WriteLine("Current data:");
        foreach (var item in data)
        {
            Console.WriteLine(item);
        }
    }
}

// Controller class
public class Controller
{
    private Model model;
    private View view;
    public Controller()
    {
        model = new Model();
        view = new View();
    }

    public void AddData(string item)
    {
        model.AddData(item);
        view.ShowData(model.GetData());
    }
}
```

```csharp
// Main class
class Program
{
    static void Main(string[] args)
    {
        Controller controller = new Controller();
        controller.AddData("Item 1");
        controller.AddData("Item 2");
    }
}
```

## Related Topics
---
- [[Design Patterns Overview]]
- 

## Resources
---
- Link
- 