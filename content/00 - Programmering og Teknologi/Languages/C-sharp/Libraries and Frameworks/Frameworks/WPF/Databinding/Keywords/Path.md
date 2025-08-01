tags: #C-sharp #Programmering #WPF #DataBinding #DataBindingKeyWords
## Definition
---
Specifies the property path to the source object’s property. 

It's used when binding to a property with a different name or when the target element is a different type from the source element.

## Example
---
```xml
<CheckBox x:Name="checkBox" Content="Show Label"/> 
<Label Content="Hello,World" Visibility="{Binding Path=IsChecked, ElementName=checkBox}"/>
```

In this example, the target element (`Label`) is of a different type from the source (`CheckBox`), and a path is used to bind the `IsChecked` property of the `CheckBox` to the `Visibility` property of the `Label`.

## Related Topics
---
- [[Source]]
- [[Target]]
- [[ElementName]]
- [[DataContext]]
- [[WPF Data Binding Overview]]