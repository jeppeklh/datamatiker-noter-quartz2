tags: #Programmering #Bash #BashControlFlow #BranchingLogic

## Definition 
---
`case` statements are used for multi-way branching based on the value of a variable.
## Syntax
---
```bash
case "$variable" in
  pattern1)
    # code to execute if variable matches pattern1
    ;;
  pattern2)
    # code to execute if variable matches pattern2
    ;;
  *)
    # code to execute if variable doesn't match any pattern
    ;;
esac
```
## Example
---
```bash
#!/bin/bash

day="Monday"

case $day in
  "Monday")
    echo "Today is Monday."
    ;;
  "Tuesday")
    echo "Today is Tuesday."
    ;;
  *)
    echo "Some other day."
    ;;
esac
```


## Related Topics
---
- [[Bash Control Flow Overview]]
- [[Bash Branching Logic]]
- [[Bash If Statements]]

## Resources
---
- Link
- 