tags: #C-sharp #Programmering #WPF #WPFControl

> [!tldr] Definition
> A CheckBox is a control that the user can select or clear. 
> It can be used for boolean input.

---

## Properties
- `IsChecked`: Gets or sets whether the CheckBox is checked. 
- `Content`: Gets or sets the content displayed next to the CheckBox.

---

## Events
- `Checked`: Occurs when the CheckBox is checked. 
- `Unchecked`: Occurs when the CheckBox is unchecked.

---

## Example
```xml
<CheckBox Content="Accept Terms and Conditions" />
```

---

#### TextChanged method Method
```c#
private void CheckBox_Checked(object sender, RoutedEventArgs e)
{
    // Handle checked event
}
```

---

## Related Topics
- Link
- 

---

## Resources
- Link
- 