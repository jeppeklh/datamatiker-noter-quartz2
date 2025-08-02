tags: #C-sharp #Programmering #WPF #WPFControl

> [!tldr] Definition
> A Button is a common control that users can click to trigger an action.

---

## Properties
- `Content`: The text or element displayed on the button. 
- `IsEnabled`: Indicates whether the button is enabled.

---

## Methods
- `OnClick`: Called when the button is clicked.

---

## Events
- `Click`: Occurs when the button is clicked.

---

## Example
```xml
<Button Content="Click Me" Click="Button_Click"/>
```

---

#### Click Event
```csharp
private void Button_Click(object sender, RoutedEventArgs e)
{
    MessageBox.Show("Button clicked!");
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