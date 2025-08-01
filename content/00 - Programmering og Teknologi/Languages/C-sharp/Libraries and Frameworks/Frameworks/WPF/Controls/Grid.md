tags: #C-sharp #Programmering #WPF #WPFControl

## Definition 
---
A Grid is a layout control that organizes its children in a tabular structure of rows and columns.

Grids are powerful for creating complex layouts. They allow precise control over the positioning of child elements.
## Properties
---
- `RowDefinitions`: Defines the rows in the grid. 
- `ColumnDefinitions`: Defines the columns in the grid.

## Example
---
```xml
<Grid> 
	<Grid.RowDefinitions> 
		<RowDefinition Height="Auto" /> 
		<RowDefinition Height="*" /> 
	</Grid.RowDefinitions> 
	
	<Grid.ColumnDefinitions> 
		<ColumnDefinition Width="Auto" /> 
		<ColumnDefinition Width="*" /> 
	</Grid.ColumnDefinitions> 
	
	<TextBlock Text="Row 0, Col 0" Grid.Row="0" Grid.Column="0" /> 
	<TextBlock Text="Row 0, Col 1" Grid.Row="0" Grid.Column="1" /> 
	<TextBlock Text="Row 1, Col 0" Grid.Row="1" Grid.Column="0" /> 
	<TextBlock Text="Row 1, Col 1" Grid.Row="1" Grid.Column="1" /> 
</Grid>
```
#### Click Event
---
```c#
private void Button_Click(object sender, RoutedEventArgs e)
{
    MessageBox.Show("Button clicked!");
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