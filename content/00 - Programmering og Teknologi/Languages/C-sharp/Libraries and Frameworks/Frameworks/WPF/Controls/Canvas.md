tags: #C-sharp #Programmering #WPF #WPFControl

> [!tldr] Definition
> A Canvas is a layout control that provides absolute positioning for its child elements. It allows precise control over where elements are placed.

The Canvas is useful for scenarios where fixed positioning of elements is required, such as in drawing applications or custom animations.

---

## Properties
- `Children`: Gets the child elements of the Canvas. 
- `Left`, `Top`, `Right`, `Bottom`: Attached properties used to position child elements.


---

## Example
```xml
<Canvas> 
	<Rectangle Canvas.Left="10" Canvas.Top="20" Width="100" Height="50" Fill="Blue"/> 
	<Ellipse Canvas.Left="150" Canvas.Top="100" Width="80" Height="80" Fill="Red"/> 
</Canvas>
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