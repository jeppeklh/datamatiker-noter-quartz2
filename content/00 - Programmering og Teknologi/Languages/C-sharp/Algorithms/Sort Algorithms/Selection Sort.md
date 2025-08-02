tags: #C-sharp #Programmering #Algorithms #SortAlgorithms 
## Overview
Selection Sort is an in-place comparison sorting algorithm. 

It divides the input list into two parts: a sorted sublist of items which is built up from left to right at the front (left) of the list, and a sublist of the remaining unsorted items. 

The algorithm proceeds by finding the smallest (or largest) element from the unsorted sublist, swapping it with the leftmost unsorted element, and moving the sublist boundaries one element to the right.

---

## Pseudokode
```csharp

function selectionSort(array)
 n = length of array
for i from 0 to n-1 do
	minIndex = i
	for j from i+1 to n-1 do
		if array[j] < array[minIndex] then
			minIndex = j
		end if
	end for
	 // Swap the minimum element with the first element of the unsorted portion
	swap(array[i], array[minIndex])
end for
return array
end function
```

---

## C-sharp
```csharp
static void sort(int []arr)
    {
        int n = arr.Length;
        // One by one move boundary of unsorted subarray
        for (int i = 0; i < n - 1; i++)
        {
            // Find the minimum element in unsorted array
            int min_idx = i;
            for (int j = i + 1; j < n; j++)
                if (arr[j] < arr[min_idx])
                    min_idx = j;
            // Swap the found minimum element with the first
            // element
            int temp = arr[min_idx];
            arr[min_idx] = arr[i];
            arr[i] = temp;
        }
    }
```

---

## Time Complexity
- Best Case: O(n²)
- Average Case: O(n²)
- Worst Case: O(n²)

---

## Space Complexity
- O(1)

---

## Related Topics
- [[Algorithms Overview]]
- [[Bubble Sort]]
- [[Quick Sort]]

---

## Resources
- [Sorting Algorithms](https://www.geeksforgeeks.org/sorting-algorithms/?ref=lbp)
- [Selection Sort](https://www.geeksforgeeks.org/selection-sort/)