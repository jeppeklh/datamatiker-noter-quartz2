tags: #C-sharp #Programmering #WPF #WPFControl

## Definition 
---
A DataGrid is a control that displays data in a customizable grid format. 
It allows for sorting, grouping, and editing of data.

DataGrids are powerful for displaying and manipulating tabular data, providing built-in support for operations like sorting and editing.
## Properties
---
- `ItemsSource`: Gets or sets the collection used to generate the content of the DataGrid.
- `Columns`: Gets the collection of columns in the DataGrid. 
- `AutoGenerateColumns`: Gets or sets a value indicating whether columns are created automatically.

## Example
---
```xml
<DataGrid AutoGenerateColumns="True" ItemsSource="{Binding YourDataSource}" />
```
#### LoadingRow Event
---
```c#
private void DataGrid_LoadingRow(object sender, DataGridRowEventArgs e)
{
    // Handle row loading event
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