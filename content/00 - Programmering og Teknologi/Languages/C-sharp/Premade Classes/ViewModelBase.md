

```csharp
public class ViewModelBase : INotifyPropertyChanged
{
    public event PropertyChangedEventHandler? PropertyChanged;

    protected void OnPropertyChanged([CallerMemberName] string propertyName = null)
    {
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
    }
}
```

## Usage
---
Used to simplfy ViewModels. 
The ViewModel now Inherits the ViewModelBase.
That way the viewmodel inherits INotifyPropertyChanged through the ViewModelBase.
Now we dont have to type out the event and the OnPropertyChanged() method in each ViewModel.
And also we dont have to give a parameter to the OnPropertyChanged Method

#### Before
```csharp
    private string title;

    public string Title
    {
        get { return title; }
        set
        {
            title = value;
            OnPropertyChanged("Title");
        }
    }

	public event PropertyChangedEventHandler? PropertyChanged;

    protected void OnPropertyChanged([CallerMemberName] string propertyName = null)
    {
        PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
    }
```

#### After
```csharp
    private string title;

    public string Title
    {
        get { return title; }
        set
        {
            title = value;
            OnPropertyChanged();
        }
    }
```

## Resources
---
[ViewModelBase Youtube Video](https://www.youtube.com/watch?v=Fs2gwb6Dqjk)