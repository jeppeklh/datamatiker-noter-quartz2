tags: #C-sharp #Programmering #WPF #DataBinding #XAMLtoXAML 
> [!tldr] Definition
> XAML to XAML data binding refers to the process of binding properties of one XAML element to properties of another XAML element.

---

## Without Codebehind
```xml
<StackPanel Margin="10">
    <TextBox Name="txtValue"/>
    <WrapPanel Margin="0,10">
        <TextBlock Text="Value: " FontWeight="Bold"/>
        <TextBlock Text="{Binding ElementName=txtValue, Path=Text}"/>
    </WrapPanel>
</StackPanel>
```
In this example, the `TextBlock`'s `Text` property is bound to the `Text` property of the `TextBox` named `txtValue`.

---

## With Codebehind
### XAML
```xml
<StackPanel Margin="10">
	<TextBox Name="txtValue"/>
	<WrapPanel Margin="0,10">
		<TextBlock Text="Value: " FontWeight="Bold"/>
		<TextBlock Name="lblValue"/>
	</WrapPanel>
</StackPanel>

```

---

### Codebehind
```csharp
public partial class CodeBehindBindingsSample : Window
{
	public CodeBehindBindingsSample() 
	{
		InitializeComponent();
		Binding binding = new Binding("Text");
		binding.Source = txtValue;
		lblValue.SetBinding(TextBlock.TextpProperty, binding);
		
	}
}
```

---

## Multibinding
MultiBinding allows binding multiple [[WPF Data Binding Overview#Source|sources]] to a single [[WPF Data Binding Overview#Target|target]] [[Properties|property]].

Rimlig kringlet (StringFormat's første curly brackets giver ingen mening men det er sådan notaionen er)
 ![[Multibinding example.png]]
Video: [[Databind 2 - XAML to XAML.mp4#t=517|Multibinding]]

---

## Related Topics
- [[WPF Data Binding Overview]]
- [[XAML to Object Data Binding]]

---

## Resources