 tags: #C-sharp #Programmering #WPF #CommandBinding

## Definition 
---
Command binding in WPF is a mechanism that allows the binding of user interface [[WPF Controls Overview|controls]] to commands defined in the application logic. 

It provides a way to implement the [[Repo/00 - Programmering og Teknologi/SoftwareArkitektur/MVVM|MVVM]] pattern, enabling separation of concerns between the UI and the application logic.
## Key Concepts
---
- **Command**: An object that implements the [[#ICommand Interface]] . It encapsulates the logic that should be executed in response to a user action. 
- **Command Binding**: The process of linking a control's `Command` property to an `ICommand` implementation. 
- **Command Parameter**: An optional parameter that can be passed to the command's execution logic.
### ICommand Interface
---
The `ICommand` interface defines two methods and one event: 
- `Execute(Object parameter)`: The method to be called when the command is executed. 

- `CanExecute(Object parameter)`: A method that determines whether the command can execute. 

- `CanExecuteChanged`: An event that is raised when the result of `CanExecute` changes.


## Example
---
### Creating a Command
---
First, define a command in the ViewModel:
```csharp
public class RelayCommand : ICommand 
{ 
	private readonly Action<object> execute; 
	private readonly Predicate<object> canExecute;
	 
	public event EventHandler CanExecuteChanged; 
	
	public RelayCommand(Action<object> execute, Predicate<object> canExecute = null) 
	{ 
		this.execute = execute; 
		this.canExecute = canExecute; 
	} 
	
	public bool CanExecute(object parameter) 
	{ 
		return this.canExecute == null || this.canExecute(parameter); 
	} 
	
	public void Execute(object parameter) 
	{ 
		this.execute(parameter); 
	} 
	
	public void RaiseCanExecuteChanged() 
	{ 
		CanExecuteChanged?.Invoke(this, EventArgs.Empty); 
	} 
}
```

### Implementing the ViewModel
---
Next, implement the ViewModel with a command [[Properties|property]]:
```csharp
public class MainViewModel
{
    public ICommand MyCommand { get; private set; }

    public MainViewModel()
    {
        MyCommand = new RelayCommand(ExecuteMyCommand, CanExecuteMyCommand);
    }

    private void ExecuteMyCommand(object parameter)
    {
        // Command execution logic
    }

    private bool CanExecuteMyCommand(object parameter)
    {
        // Command can execute logic
        return true;
    }
}
```

### Binding the Command in XAML
---
Finally, bind the command to a control in XAML:
```xml
<Window x:Class="WpfApp.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        DataContext="{Binding MainViewModel, Source={StaticResource Locator}}">
    <Grid>
        <Button Content="Execute Command"
                Command="{Binding MyCommand}"
                CommandParameter="SomeParameter"/>
    </Grid>
</Window>
```
## Related Topics
---
- Link
- 

## Resources
---
- [[Commandbind 1 - Intro.mp4]]
- [[CommandBind 2 - ListBox.mp4]]
- [[CommandBind 3 - Button.mp4]]