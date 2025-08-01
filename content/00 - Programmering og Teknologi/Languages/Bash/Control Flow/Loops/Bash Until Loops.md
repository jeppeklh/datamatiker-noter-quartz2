tags: #Programmering #Bash #BashControlFlow #Loops 

## Definition 
---
`until` loops are similar to [[Bash While Loops|while loops]], but the code block executes until the condition becomes true.
## Syntax
---
```bash
until [ condition ]
do
  # code to execute
done
```
## Example
---
```bash
#!/bin/bash

counter=1

until [ $counter -gt 5 ]
do
  echo "Counter: $counter"
  ((counter++))
done
```

## Related Topics
---
- [[Bash Loops]]
- [[Bash For Loops]]
- [[Bash While Loops]]
- [[Bash Operators]]

## Resources
---
- Link
- 