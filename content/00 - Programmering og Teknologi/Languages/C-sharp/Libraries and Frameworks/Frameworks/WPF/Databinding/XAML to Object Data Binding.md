tags: #C-sharp #Programmering #WPF #DataBinding #XAMLtoObject
## Definition
---
XAML to object data binding refers to the process of binding properties of a XAML element to [[Properties|properties]] of an [[Objects|object]], often a view model in the [[Repo/00 - Programmering og Teknologi/SoftwareArkitektur/MVVM|MVVM]] pattern.

## Example
---
### XAML
---
```xml
<Grid>
	<Label Content="{Binding Path=FullName}" HorizontalAlignment="Left" Margin="121,40,0,0"/>
	<TextBox x:Name="firstName" Text="{Binding Path=FirstName, UpdateSourceTrigger=PropertyChanged}"/>
	<TextBox x:Name="lastName" Text="{Binding Path=LastName}"/>
	<Button Content="Update" HorizontalAlignment="Left" Height="46" Widt="120"/>	
</Grid>
```
### Codebehind
---
```csharp
public class MainViewModel : INotifyPropertyChanged
{
	private string firstName = "Jan";
	public string FirstName
	{
		get { return firstName; }
		set 
		{
			firstName = value;
			OnPropertyChanged("FirstName");
		}
	}
	private string lastName = "Brown";
	public string LastName
	{
		get { return lastName; }
		set { lastName = value; }
	}

public event PropertyChangedEventHandler PropertyChanged;

protected void OnPropertyCanged(string name)
{
	PropertyChangedEventHandler handler = PropertyChanged;
	if(handler != null)
	{
		handler(this, new PropertyChangedEventArgs(name));
	}
}
}
```

#### FullName
---
Hvis hvis man vil have fullname. Altså en tredje property der concatinerer firstname og lastname

```csharp
public class MainViewModel : INotifyPropertyChanged
{
	private string firstName = "Jan";
	public string FirstName
	{
		get { return firstName; }
		set 
		{
			firstName = value;
			OnPropertyChanged("FirstName");
			OnPropertyChanged("FullName");
		}
	}
	private string lastName = "Brown";
	public string LastName
	{
		get { return lastName; }
		set 
		{ 
			lastName = value;
			OnPropertyChanged("FirstName");
			OnPropertyChanged("FullName"); 
		}
	}
	public string FullName
	{
		get { return firstName + lastName; }
	}
}
```

## Related Topics
---
- [[WPF Data Binding Overview]]
- [[XAML to XAML Data Binding]]
## Resources
---