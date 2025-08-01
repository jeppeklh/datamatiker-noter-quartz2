tags: #C-sharp #Programmering #WPF #WPFControl

## Definition 
---
A ProgressBar is a control that indicates the progress of an operation. It can be determinate or indeterminate.

ProgressBars are useful for indicating the status of operations, such as file downloads or data processing.
## Properties
---
- `Minimum`: Gets or sets the minimum value of the range. 
- `Maximum`: Gets or sets the maximum value of the range. 
- `Value`: Gets or sets the current value of the ProgressBar. 
- `IsIndeterminate`: Gets or sets a value indicating whether the ProgressBar shows a repeating pattern.

## Example
---
```xml
<ProgressBar Minimum="0" Maximum="100" Value="50" />
```
#### C-Sharp
---
```csharp
// Update progress
progressBar.Value = 75;
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