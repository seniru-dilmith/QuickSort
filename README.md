
# Quick Sort in C++

## Introduction

Quick Sort is a divide-and-conquer algorithm. It works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays according to whether they are less than or greater than the pivot. The sub-arrays are then sorted recursively.

## Code Explanation

Below is the C++ implementation of the Quick Sort algorithm with detailed comments.

```cpp
#include <iostream>
#include <vector>

// Function to swap two elements
void swap(int& a, int& b) {
    int temp = a;
    a = b;
    b = temp;
}

// Partition function to place the pivot element at its correct position
// and place all smaller elements to the left of the pivot and all larger elements to the right
int partition(std::vector<int>& arr, int low, int high) {
    int pivot = arr[high]; // Choosing the last element as the pivot
    int i = low - 1; // Index of the smaller element

    for (int j = low; j <= high - 1; ++j) {
        // If the current element is smaller than the pivot
        if (arr[j] < pivot) {
            ++i; // Increment the index of the smaller element
            swap(arr[i], arr[j]); // Swap the current element with the element at index i
        }
    }
    // Swap the pivot element with the element at index i+1
    swap(arr[i + 1], arr[high]);
    return i + 1; // Return the partitioning index
}

// Quick Sort function
void quickSort(std::vector<int>& arr, int low, int high) {
    if (low < high) {
        // pi is the partitioning index, arr[pi] is now at the right place
        int pi = partition(arr, low, high);

        // Recursively apply the same logic to the left and right subarrays
        quickSort(arr, low, pi - 1); // Before pi
        quickSort(arr, pi + 1, high); // After pi
    }
}

// Utility function to print the array
void printArray(const std::vector<int>& arr) {
    for (int i = 0; i < arr.size(); ++i) {
        std::cout << arr[i] << " ";
    }
    std::cout << std::endl;
}

int main() {
    std::vector<int> arr = {10, 80, 30, 90, 40, 50, 70};
    int n = arr.size();
    std::cout << "Original array: ";
    printArray(arr);

    quickSort(arr, 0, n - 1);

    std::cout << "Sorted array: ";
    printArray(arr);
    return 0;
}
```

## Explanation

1. **swap Function**:
   - This function takes two integer references and swaps their values.

2. **partition Function**:
   - This function takes the array, the starting index (`low`), and the ending index (`high`).
   - It chooses the last element as the pivot.
   - It rearranges the array so that all elements less than the pivot are on the left, and all elements greater than the pivot are on the right.
   - It returns the index of the pivot element after partitioning.

3. **quickSort Function**:
   - This function takes the array, the starting index (`low`), and the ending index (`high`).
   - It recursively sorts the sub-arrays before and after the partitioning index.

4. **printArray Function**:
   - This utility function prints the elements of the array.

5. **main Function**:
   - This is the entry point of the program.
   - It initializes an array, prints the original array, calls the `quickSort` function, and then prints the sorted array.

## Conclusion

Quick Sort is an efficient sorting algorithm with an average time complexity of O(n log n). This C++ implementation demonstrates the core concepts of the algorithm, including partitioning and recursive sorting of sub-arrays.
