tags: #Programmering #Bash #BashBasics 

## Definition 
---
**Operators** in Bash are used to perform operations on [[Bash Variables and Assignment]] and values.

## Types of Operators:
---
- **Arithmetic Operators**: `+ - * / %`
- **Comparison Operators**: `-eq -ne -gt -lt -ge -le`
- **Logical Operators**: `&& || !`
- **String Operators**: `= != -z -n`
#### Comparison Operators
---
- `-eq`: is equal to
- `-ne`: is not equal to
- `-gt`: is greater than
- `-lt`: is less than
- `-ge`: is greater than or equal to
- `-le`: is less than or equal to
##### Example
---
```bash
#!/bin/bash

a=10
b=20

# Arithmetic
sum=$((a + b))
echo $sum

# Comparison
if [ $a -eq $b ]; then
  echo "a is equal to b"
else
  echo "a is not equal to b"
fi

# Logical
if [ $a -lt 15 ] && [ $b -gt 15 ]; then
  echo "Both conditions are true"
fi
```
#### String Operators
---
- **`-z`**: Tests if the length of a string is zero.
- **`-n`**: Tests if the length of a string is non-zero.
##### Example
---
```bash
#!/bin/bash

empty_string=""
non_empty_string="Hello"

if [ -z "$empty_string" ]; then
  echo "The string is empty."
else
  echo "The string is not empty."
fi

if [ -z "$non_empty_string" ]; then
  echo "The string is empty."
else
  echo "The string is not empty."
fi
```

## Related Topics
---
- [[Bash Syntax]]
- [[Bash Variables and Assignment]]
- [[Bash Data Types]]

## Resources
---
- Link
- 