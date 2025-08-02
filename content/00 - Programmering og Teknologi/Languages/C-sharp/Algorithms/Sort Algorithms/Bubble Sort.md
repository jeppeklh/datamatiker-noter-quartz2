tags: #C-sharp #Programmering #Algorithms #SortAlgorithms 
## Overview
Bubble Sort is a simple sorting algorithm that works by repeatedly stepping through the list to be sorted, comparing each pair of adjacent items and swapping them if they are in the wrong order. The pass through the list is repeated until no swaps are needed.

---

## Psudokode
```csharp
function bubbleSort(array)
	n = length of array
	for i from 0 to n-1 do
		`for j from 0 to n-i-1 do`
			`if array[j] > array[j+1] then`
				`// Swap the elements`

				`temp = array[j]`
				`array[j] = array[j+1]`
				`array[j+1] = temp`
			`end if`
		`end for`
	`end for`
`return array`
`end function`
```

J < N - I -1
Når I = 1 (hele arrayet)
Når I = 2 (Hele arrayet på nær det sidste element (Er allerede på rette plads))
Når I = 3 (Hele arrayet på nær de 2 sidste elemetner)
Osv.

---

## C-sharp
```csharp
static void bubbleSort(int[] arr, int n)
    {
        int i, j, temp;
        bool swapped;
        for (i = 0; i < n - 1; i++) {
            swapped = false;
            for (j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    // Swap arr[j] and arr[j+1]
                    temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swapped = true;
                }
            }
            // If no two elements were
            // swapped by inner loop, then break
            if (swapped == false)
                break;
        }
    }
```

 Swapped
For ikke at behøve at løbe arrayet igennem hvis swapped == false (Hele arrayet er sorted)

---

## Time Complexity
- Best Case: O(n)
- Average Case: O(n²)
- Worst Case: O(n²)

---

## Space Complexity
- O(1)

---

## Related Topics
- [[Algorithms Overview]]
- [[Quick Sort]]
- [[Selection Sort]]

---

## Resources
- [Sorting Algorithms](https://www.geeksforgeeks.org/sorting-algorithms/?ref=lbp)
- [Bubble Sort](https://www.geeksforgeeks.org/bubble-sort/)
