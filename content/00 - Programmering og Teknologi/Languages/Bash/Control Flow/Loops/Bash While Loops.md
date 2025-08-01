tags: #Programmering #Bash #BashControlFlow #Loops 

## Definition 
---
`while` loops are used to execute a block of code as long as a condition is true.
## Syntax
---
```bash
while [ condition ]
do
  # code to execute
done
```
## Example
---
```bash
#!/bin/bash

counter=1

while [ $counter -le 5 ]
do
  echo "Counter: $counter"
  ((counter++))
done

```



## Related Topics
---
- [[Bash Loops]]
- [[Bash For Loops]]
- [[Bash Until Loops]]
- [[Bash Operators]]

## Resources
---
- Link
- 