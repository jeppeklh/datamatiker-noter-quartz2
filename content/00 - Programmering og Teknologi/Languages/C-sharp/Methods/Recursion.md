tags: #C-sharp #Programmering #Methods #Recursion

## Definition 
---
Recursion is a programming technique where a [[Methods Overview|method]] calls itself in order to solve a problem. 

It is a common approach for problems that can be broken down into simpler, smaller subproblems of the same type.
## Base case and Recursive case
---
- **Base Case**: The condition where recursive [[Methods Overview|method]] stops calling itself, preventing an infinite [[Loops|loop]]

- **Recursive Case**: The part of the [[Methods Overview|method]] where it calls itself to break the problem down into smaller subproblems.
### Example
```csharp
public int Fibonacci(int n)
{
    if (n <= 1) // Base case
    {
        return n;
    }
    else
    {
        return Fibonacci(n - 1) + Fibonacci(n - 2); // Recursive case
    }
}
```

## When to Use Recursion
---
- Problems that can be broken down into smaller, similar subproblems.
- Tree and graph traversal problems.
- Divide-and-conquer [[Algorithms Overview|algorithms]] like Quicksort, Mergesort and Binary Search.
- Situations where the recursive solution is simpler and more intuitive than an iterative one.


## Related Topics
---
- [[Defining Methods]]
- [[Overloading]]
- [[Control Flows]]

## Resources
---
- [Recursion](https://www.geeksforgeeks.org/recursion-in-c-sharp/)
- [Tower of Hanoi](https://www.geeksforgeeks.org/c-program-for-tower-of-hanoi/?ref=lbp)