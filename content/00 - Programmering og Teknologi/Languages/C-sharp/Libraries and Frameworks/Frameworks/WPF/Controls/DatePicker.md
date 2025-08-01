tags: #C-sharp #Programmering #WPF #WPFControl

## Definition 
---
A DatePicker is a control that allows users to select a date from a calendar or by typing.

DatePickers are useful for applications that require date input, such as scheduling or reservation systems.
## Properties
---
- `SelectedDate`: Gets or sets the currently selected date. 
- `DisplayDateStart`: Gets or sets the first date to be displayed. 
- `DisplayDateEnd`: Gets or sets the last date to be displayed.

## Example
---
```xml
<DatePicker SelectedDate="{Binding YourDate}" />
```
#### SelectedDateChanged Event
---
```c#
private void DatePicker_SelectedDateChanged(object sender, SelectionChangedEventArgs e)
{
    // Handle date changed event
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