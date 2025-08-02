tags: #C-sharp #Programmering #WPF #WPFControl

> [!tldr] Definition
> A TextBox is a control that allows the user to input text.

TextBox controls are essential for forms and data entry applications.

---

## Properties
- `Text`: Gets or sets the text content of the TextBox. 
- `IsReadOnly`: Gets or sets a value indicating whether the text box is read-only. 
- `MaxLength`: Gets or sets the maximum number of characters that can be manually entered into the text box.

---

## Methods
- `Clear()`: Clears all the text in the TextBox. 
- `SelectAll()`: Selects all text in the TextBox.

---

## Events
- `TextChanged`: Occurs when the text is changed.

---

## Example
```xml
`<TextBox Text="Hello, World!" Width="200" />`
```
#### TextChanged Event.
```c#
private void TextBox_TextChanged(object sender, TextChangedEventArgs e) 
{ 
	// Handle text changed event
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