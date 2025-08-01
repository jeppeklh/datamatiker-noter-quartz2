tags: #C-sharp #Programmering #WPF #WPFControl

## Definition 
---
A RadioButton is a control that allows the user to select a single option from a group of options.
RadioButtons are typically used in groups to allow users to select one option from a set.
## Properties
---
- `IsChecked`: Gets or sets whether the RadioButton is checked. 
- `GroupName`: Gets or sets the name that specifies which RadioButton controls are mutually exclusive.

## Events
---
- `Checked`: Occurs when the RadioButton is checked.

## Example
---
```xml
<RadioButton GroupName="Gender" Content="Male" /> 
<RadioButton GroupName="Gender" Content="Female" />
```
#### Checked Event
---
```c#
private void RadioButton_Checked(object sender, RoutedEventArgs e)
{
    // Handle checked event
}
}
```
## Related Topics
---
- Link
- 

## Resources
---
- Link
- 