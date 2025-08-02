tags: #C-sharp #Programmering #Algorithms #SortAlgorithms 

## Overview
Quick Sort is an efficient sorting algorithm. 

It uses a divide-and-conquer strategy to divide a list into two sublists: the low elements and the high elements. 

Quick Sort can then [[Recursion|recursively]] sort the sublists.

---

## Pseudo code
```csharp
function quickSort(array, low, high)
if low < high then
	// Partition the array and get the pivot index
	pivotIndex = partition(array, low, high)
	// Recursively sort the subarrays before and after the pivot
	quickSort(array, low, pivotIndex - 1)
	quickSort(array, pivotIndex + 1, high)
 end if end function
 
function partition(array, low, high)
// Choose the pivot element (usually the last element)
pivot = array[high]
// Initialize the index of the smaller element
 i = low - 1
for j from low to high - 1 do
	// If current element is smaller than or equal to pivot
	 if array[j] <= pivot then
		 // Increment index of smaller element
		 i = i + 1
		// Swap array[i] and array[j]
		 swap(array[i], array[j])
	end if
end for
// Swap array[i+1] and array[high] (or pivot)
swap(array[i+1], array[high])
// Return the partition index
return i + 1 end function
```

---

## C-sharp
```csharp
static void swap(int[] arr, int i, int j)  
{
	int temp = arr[i];       
	arr[i] = arr[j];       
	arr[j] = temp;
 } 
// This function takes last element as pivot,   
// places the pivot element at its correct position  
// in sorted array, and places all smaller to left   
// of pivot and all greater elements to right of pivot   

static int partition(int[] arr, int low, int high)
    {     
	// Choosing the pivot       
	int pivot = arr[high];      
	 // Index of smaller element and indicates      
	// the right position of pivot found so far   
	   
	 int i = (low - 1);      
	 for (int j = low; j <= high - 1; j++)
	{          
		 // If current element is smaller than the pivot          
		 if (arr[j] < pivot)
		{              
			 // Increment index of smaller element              
			 i++;               
			swap(arr, i, j);          
		 }      
	 }       
	swap(arr, i + 1, high);      
	return (i + 1);  
}  

 // The main function that implements QuickSort   
// arr[] --> Array to be sorted,  
// low --> Starting index,  
// high --> Ending index  

static void quickSort(int[] arr, int low, int high)  
	{      
	if (low < high)
	{          
		// pi is partitioning index, arr[p]          
		// is now at right place`          
		int pi = partition(arr, low, high);          
		// Separately sort elements before          
		// and after partition index
		           
		quickSort(arr, low, pi - 1);           
		quickSort(arr, pi + 1, high);       
	}   
}
```

---

## Time Complexity
- Best Case: O(n log n)
- Average Case: O(n log n)
- Worst Case: O(n²)

---

## Space Complexity
- O(log n)

---

## Related Topics
- [[Algorithms Overview]]
- [[Bubble Sort]]
- [[Selection Sort]]
- [[Recursion]]

---

## Resources
- [Sorting Algorithms](https://www.geeksforgeeks.org/sorting-algorithms/?ref=lbp)
- [Quick Sort](https://www.geeksforgeeks.org/quick-sort/)