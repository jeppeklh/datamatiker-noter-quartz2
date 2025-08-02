tags: #C-sharp #Programmering #WPF #WPFControl

> [!tldr] Definition
> A Slider is a control that allows users to select a value from a continuous or discrete range by moving a thumb along a track.

Sliders are commonly used for adjusting settings, such as volume or brightness, where a range of values is required.

---

## Properties
- `Minimum`: Gets or sets the minimum value of the range. 
- `Maximum`: Gets or sets the maximum value of the range. 
- `Value`: Gets or sets the current value of the Slider.

---

## Methods
- `OnClick`: Called when the button is clicked.

---

## Events
- `Click`: Occurs when the button is clicked.

---

## Example
```xml
<Slider Minimum="0" Maximum="100" Value="50" />
```

---

#### Click Event
```csharp
private void Slider_ValueChanged(object sender, RoutedPropertyChangedEventArgs<double> e)
{
    // Handle value changed event
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