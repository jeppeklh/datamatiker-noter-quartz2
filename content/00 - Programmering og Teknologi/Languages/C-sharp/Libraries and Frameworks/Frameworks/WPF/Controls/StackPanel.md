tags: #C-sharp #Programmering #WPF #WPFControl

> [!tldr] Definition
> A StackPanel is a layout control that arranges its child elements into a single line that can be oriented horizontally or vertically.

StackPanels are simple and efficient for basic layouts, where child elements are stacked in a single direction.

---

## Properties
- `Orientation`: Gets or sets the orientation of children elements, either Horizontal or Vertical.

---

## Example
```xml
<StackPanel Orientation="Vertical"> 
	<TextBlock Text="Item 1" /> 
	<TextBlock Text="Item 2" /> 
	<TextBlock Text="Item 3" /> 
</StackPanel>
```

---

#### Click Event
```c#
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