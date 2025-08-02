tags: #C-sharp #Programmering #Algorithms #SearchAlgorithms
## Overview

Binary Search is a search algorithm that finds the position of a target value within a sorted array. Binary Search compares the target value to the middle element of the array. If they are not equal, the half in which the target cannot lie is eliminated, and the search continues on the remaining half until it is successful or the remaining half is empty.

---

#### Pesudo code
```csharp
function binarySearch(array, target)
	left = 0
	right = length of array - 1
	while left <= right do
		mid = (left + right) / 2
		// If the target is found at the middle
		if array[mid] = target then
			return mid
		// If the target is greater, ignore the left half
		else if array[mid] < target then
			left = mid + 1
		// If the target is smaller, ignore the right half
		else right = mid - 1
	end while
	// If the target is not found
	return -1
end function
```

---

#### C-sharp
```csharp
public static int binary(int[] arr, int x)
  {
    int start = 0;
    int end = arr.Length - 1;
    while (start <= end) {
        int mid = (start + end) / 2;
        if (x == arr[mid]) {
            return mid;
        }
        else if (x > arr[mid]) {
            start = mid + 1;
        }
        else {
            end = mid - 1;
        }
    }
    return -1;
  }
```

---

## Time Complexity
- Best Case: O(1)
- Average Case: O(log n)
- Worst Case: O(log n)

---

## Space Complexity
- O(1)

---

## Related Topics
- [[Algorithms Overview]]

---

## Resources
- [Binary Search](https://www.geeksforgeeks.org/binary-search/?ref=lbp)
- [Linear Search vs Binary Search](https://www.geeksforgeeks.org/linear-search-vs-binary-search/?ref=lbp)