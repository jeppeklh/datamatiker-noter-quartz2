tags: #C-sharp #Programmering #WPF #DataBinding #DataBindingKeyWords
> [!tldr] Definition
> Used to refer to another XAML element by its name value. It specifies the source element in the binding.

---

## Example
```xml
<CheckBox x:Name="checkBox" Content="Show Label"/> 
<Label Content="Hello,World" Visibility="{Binding Path=IsChecked, ElementName=checkBox}"/>
```
In this example, `ElementName=checkBox` is used to refer to the `CheckBox` named `checkBox`.

---

## Related Topics
- [[Source]]
- [[Target]]
- [[Path]]
- [[DataContext]]
- [[WPF Data Binding Overview]]