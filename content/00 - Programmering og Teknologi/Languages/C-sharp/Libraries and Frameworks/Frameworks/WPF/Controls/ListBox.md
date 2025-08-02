tags: #C-sharp #Programmering #WPF #WPFControl

> [!tldr] Definition
> A ListBox is a control that provides a list of selectable items. 
> Users can select one or multiple items from the list.

ListBoxes are ideal for presenting a list of items where multiple selection or complex item templates are required.

---

## Properties
- `ItemsSource`: Gets or sets the collection used to generate the content of the ListBox. 
- `SelectedItem`: Gets or sets the currently selected item. 
- `SelectionMode`: Gets or sets the selection behavior, such as Single or Multiple.

---

## Example
```xml
<ListBox SelectionMode="Multiple"> 
	<ListBoxItem>Item 1</ListBoxItem> 
	<ListBoxItem>Item 2</ListBoxItem> 
	<ListBoxItem>Item 3</ListBoxItem> 
</ListBox>
```

---

#### SelectionChanged Event
```c#
private void ListBox_SelectionChanged(object sender, SelectionChangedEventArgs e) { 
	// Handle selection changed event 
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