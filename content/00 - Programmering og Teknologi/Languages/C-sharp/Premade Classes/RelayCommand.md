> [!tldr] Definition
> For making the usage of comands easier.

```csharp
public class RelayCommand : ICommand
{
    private Action<object> execute;
    private Func<object, bool> canExecute;

    public event EventHandler? CanExecuteChanged
    {
        add { CommandManager.RequerySuggested += value; }
        remove { CommandManager.RequerySuggested -= value; }
    }

    public RelayCommand(Action<object> execute, Func<object, bool> canExecute = null)
    {
        this.execute = execute;
        this.canExecute = canExecute;
    }


    public bool CanExecute(object? parameter)
    {
        return canExecute == null || canExecute(parameter);
    }

    public void Execute(object? parameter)
    {
        execute(parameter);
    }
}
```

---

## How to use it
CanExecute alwas true.
```csharp
 public RelayCommand NameOfCommand => new RelayCommand(execute => MyMethodName(), canExecute => { return true; });
```

CanExecute determined by a method we define that returns a boolean.
```csharp
 public RelayCommand NameOfCommand => new RelayCommand(execute => MyMethodName(), canExecute => CanExecuteMethod());
```