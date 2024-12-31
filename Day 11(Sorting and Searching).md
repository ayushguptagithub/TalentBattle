### **Sorting Overview**
Sorting is the process of arranging the elements of a dataset in a specific order, such as ascending or descending. Sorting is a fundamental operation in computer science, used in searching, organizing data, and solving complex problems efficiently.

---

### **Types of Sorting Algorithms**
Sorting algorithms are categorized based on their performance, stability, and approach:

1. **Comparison-based Sorting**:
   - Examples: Bubble Sort, Selection Sort, Insertion Sort, Merge Sort, Quick Sort
   - They compare pairs of elements to decide their order.

2. **Non-comparison Sorting**:
   - Examples: Counting Sort, Radix Sort, Bucket Sort
   - They use techniques based on counting or hashing.

3. **Stability**:
   - Stable algorithms preserve the relative order of equal elements.
   - Examples: Merge Sort, Bubble Sort
   - Unstable: Quick Sort, Selection Sort

4. **Complexity**:
   - Best: \( O(n \log n) \)
   - Average: \( O(n^2) \), \( O(n \log n) \)
   - Worst: \( O(n^2) \)

---

### **Sorting Algorithms with Explanation**

---

### **1. Bubble Sort**
**Theory**:
Bubble Sort repeatedly compares adjacent elements and swaps them if they are in the wrong order. After each iteration, the largest element bubbles up to the end.

- **Best Case**: \( O(n) \) (already sorted)
- **Worst Case**: \( O(n^2) \)
- **Stable**: Yes

**Code and Explanation**:

```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {  // Outer loop for passes
        for (int j = 0; j < n - i - 1; j++) {  // Compare adjacent elements
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);  // Swap if in wrong order
            }
        }
    }
}

void displayArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    displayArray(arr, n);

    bubbleSort(arr, n);

    cout << "Sorted array: ";
    displayArray(arr, n);

    return 0;
}
```

- **Explanation**:
  - The outer loop runs \( n-1 \) passes to ensure the largest elements bubble up.
  - In the inner loop, adjacent elements are compared and swapped if the left is greater than the right.

---

### **2. Selection Sort**
**Theory**:
Selection Sort finds the smallest element in the unsorted part and swaps it with the first element of that part.

- **Best Case**: \( O(n^2) \)
- **Worst Case**: \( O(n^2) \)
- **Stable**: No

**Code and Explanation**:

```cpp
#include <iostream>
using namespace std;

void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {  // Outer loop for passes
        int minIndex = i;  // Assume the current index is the smallest
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;  // Update index of smallest element
            }
        }
        swap(arr[i], arr[minIndex]);  // Swap the smallest with current position
    }
}

void displayArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    displayArray(arr, n);

    selectionSort(arr, n);

    cout << "Sorted array: ";
    displayArray(arr, n);

    return 0;
}
```

- **Explanation**:
  - Find the smallest element in each pass.
  - Swap it with the first unsorted position.
  - Repeat for the next unsorted segment.

---

### **3. Insertion Sort**
**Theory**:
Insertion Sort builds the sorted array one element at a time by inserting the current element into the correct position.

- **Best Case**: \( O(n) \) (already sorted)
- **Worst Case**: \( O(n^2) \)
- **Stable**: Yes

**Code and Explanation**:

```cpp
#include <iostream>
using namespace std;

void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];  // Current element to insert
        int j = i - 1;

        while (j >= 0 && arr[j] > key) {  // Shift elements greater than key
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;  // Insert the key
    }
}

void displayArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    displayArray(arr, n);

    insertionSort(arr, n);

    cout << "Sorted array: ";
    displayArray(arr, n);

    return 0;
}
```

- **Explanation**:
  - For each element, find its position in the sorted portion.
  - Shift elements to make space for the new element.

---

### **4. Quick Sort**
**Theory**:
Quick Sort selects a pivot element, partitions the array, and sorts each partition recursively.

- **Best Case**: \( O(n \log n) \)
- **Worst Case**: \( O(n^2) \) (if pivot is the smallest or largest element)
- **Stable**: No

**Code**:
```cpp
#include <iostream>
using namespace std;

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;

    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[i + 1], arr[high]);
    return i + 1;
}

void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

void displayArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    displayArray(arr, n);

    quickSort(arr, 0, n - 1);

    cout << "Sorted array: ";
    displayArray(arr, n);

    return 0;
}
```

### **Merge Sort**

**Theory**:
Merge Sort is a **divide-and-conquer** algorithm that splits the array into halves, recursively sorts each half, and then merges the sorted halves back together. It is efficient for large datasets.

- **Best Case**: \( O(n \log n) \)
- **Worst Case**: \( O(n \log n) \)
- **Stable**: Yes
- **Space Complexity**: \( O(n) \) (uses additional arrays for merging)

---

### **Steps in Merge Sort**
1. **Divide**: The array is divided into two halves until each sub-array contains one element.
2. **Conquer**: Recursively sort the sub-arrays.
3. **Combine**: Merge the sorted sub-arrays to form a sorted array.

---

### **Code with Explanation**

```cpp
#include <iostream>
using namespace std;

// Function to merge two halves
void merge(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;  // Size of the left sub-array
    int n2 = right - mid;     // Size of the right sub-array

    int leftArr[n1], rightArr[n2];  // Temporary arrays

    // Copy data to temporary arrays
    for (int i = 0; i < n1; i++) {
        leftArr[i] = arr[left + i];
    }
    for (int i = 0; i < n2; i++) {
        rightArr[i] = arr[mid + 1 + i];
    }

    // Merge the temporary arrays back into the original array
    int i = 0, j = 0, k = left;  // Initial indexes for left, right, and merged array
    while (i < n1 && j < n2) {
        if (leftArr[i] <= rightArr[j]) {
            arr[k] = leftArr[i];
            i++;
        } else {
            arr[k] = rightArr[j];
            j++;
        }
        k++;
    }

    // Copy any remaining elements of leftArr
    while (i < n1) {
        arr[k] = leftArr[i];
        i++;
        k++;
    }

    // Copy any remaining elements of rightArr
    while (j < n2) {
        arr[k] = rightArr[j];
        j++;
        k++;
    }
}

// Function to perform Merge Sort
void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;  // Find the midpoint

        // Recursively sort the two halves
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        // Merge the sorted halves
        merge(arr, left, mid, right);
    }
}

// Function to display the array
void displayArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: ";
    displayArray(arr, n);

    mergeSort(arr, 0, n - 1);

    cout << "Sorted array: ";
    displayArray(arr, n);

    return 0;
}
```

### **Searching**

Searching is the process of finding the location of a specific element in a collection (like an array, linked list, etc.). There are two primary types of searching techniques:

---

### **1. Linear Search**

**Theory**:  
- Linear search checks each element in the collection one by one until the desired element is found or the entire collection is traversed.
- Works for both sorted and unsorted arrays.

**Complexity**:  
- **Best Case**: \( O(1) \) (element found at the first position)  
- **Worst Case**: \( O(n) \) (element not present or found at the last position)

---

#### **Code for Linear Search in C++**

```cpp
#include <iostream>
using namespace std;

int linearSearch(int arr[], int n, int target) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == target) {
            return i;  // Return the index of the target element
        }
    }
    return -1;  // Target not found
}

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int n = sizeof(arr) / sizeof(arr[0]);
    int target = 30;

    int result = linearSearch(arr, n, target);
    if (result != -1) {
        cout << "Element found at index: " << result << endl;
    } else {
        cout << "Element not found!" << endl;
    }

    return 0;
}
```

---

### **2. Binary Search**

**Theory**:  
- Binary search is a more efficient search technique for sorted collections.
- It divides the collection into two halves and eliminates one half in each step based on comparisons.

**Complexity**:  
- **Best Case**: \( O(1) \) (middle element is the target)  
- **Worst Case**: \( O(\log n) \) (dividing collection repeatedly)

**Steps**:  
1. Find the middle element of the collection.
2. If the target is equal to the middle element, return its index.
3. If the target is smaller, search in the left half; if larger, search in the right half.
4. Repeat until the target is found or the collection is exhausted.

---

#### **Code for Binary Search in C++**

```cpp
#include <iostream>
using namespace std;

int binarySearch(int arr[], int n, int target) {
    int left = 0, right = n - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (arr[mid] == target) {
            return mid;  // Return the index of the target element
        } else if (arr[mid] < target) {
            left = mid + 1;  // Target is in the right half
        } else {
            right = mid - 1;  // Target is in the left half
        }
    }
    return -1;  // Target not found
}

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int n = sizeof(arr) / sizeof(arr[0]);
    int target = 30;

    int result = binarySearch(arr, n, target);
    if (result != -1) {
        cout << "Element found at index: " << result << endl;
    } else {
        cout << "Element not found!" << endl;
    }

    return 0;
}
```

---

### **Key Differences Between Linear and Binary Search**

| Feature            | Linear Search                 | Binary Search                     |
|--------------------|-------------------------------|-----------------------------------|
| **Data Requirement** | Works on unsorted data         | Requires sorted data               |
| **Complexity**      | \( O(n) \)                     | \( O(\log n) \)                   |
| **Approach**        | Sequential                     | Divide and conquer                |
| **Use Case**        | Small datasets or unsorted data | Large datasets, sorted data       |

---

### **Example Walkthrough for Binary Search**
#### Given Array: \[10, 20, 30, 40, 50\], Target = 30
1. Initial range: left = 0, right = 4, mid = \( 0 + (4 - 0) / 2 = 2 \).  
   Mid element = arr[2] = 30 (Target found).  
   Return index 2.

#### Given Array: \[10, 20, 30, 40, 50\], Target = 40
1. Initial range: left = 0, right = 4, mid = \( 0 + (4 - 0) / 2 = 2 \).  
   Mid element = arr[2] = 30 (Target > Mid).  
   Update left = mid + 1 = 3.
2. New range: left = 3, right = 4, mid = \( 3 + (4 - 3) / 2 = 3 \).  
   Mid element = arr[3] = 40 (Target found).  
   Return index 3.

---

### **Conclusion**
- **Linear Search**: Use when data is unsorted or for small datasets.
- **Binary Search**: Use for sorted and large datasets for better performance.



### **Fibonacci Search**

### Code:
```cpp
#include <iostream>
using namespace std;

int fibonacciSearch(int arr[], int n, int x) {
    // Initialize Fibonacci numbers
    int fib2 = 0; // (k-2)th Fibonacci number
    int fib1 = 1; // (k-1)th Fibonacci number
    int fib = fib2 + fib1; // k-th Fibonacci number

    // Find the smallest Fibonacci number greater or equal to n
    while (fib < n) {
        fib2 = fib1;
        fib1 = fib;
        fib = fib2 + fib1;
    }

    // Marks the eliminated range from the front
    int offset = -1;

    // While there are elements to be inspected
    while (fib > 1) {
        // Check if fib2 is a valid location
        int i = min(offset + fib2, n - 1);

        // If x is greater than the value at index fib2, cut the subarray array from offset to i
        if (arr[i] < x) {
            fib = fib1;
            fib1 = fib2;
            fib2 = fib - fib1;
            offset = i;
        }
        // If x is smaller than the value at index fib2, cut the subarray after i+1
        else if (arr[i] > x) {
            fib = fib2;
            fib1 = fib1 - fib2;
            fib2 = fib - fib1;
        }
        // Element found
        else {
            return i;
        }
    }

    // Compare the last element with x
    if (fib1 && arr[offset + 1] == x) {
        return offset + 1;
    }

    // Element not found
    return -1;
}

int main() {
    int arr[] = {10, 22, 35, 40, 45, 50, 80, 82, 85, 90, 100};
    int n = sizeof(arr) / sizeof(arr[0]);
    int x = 85;

    int index = fibonacciSearch(arr, n, x);

    if (index >= 0) {
        cout << "Element found at index: " << index << endl;
    } else {
        cout << "Element not found!" << endl;
    }

    return 0;
}
```

### Explanation:
1. **Fibonacci Numbers**: 
   - A Fibonacci sequence is used to divide the array into sections for searching.
   
2. **Steps**:
   - The smallest Fibonacci number greater than or equal to the size of the array is determined.
   - The array is then divided into sections according to Fibonacci ratios.
   - The search compares the target with elements at these sections and eliminates parts of the array.

3. **Time Complexity**:
   - The average case is \(O(\log n)\).

### Example Output:
For the input array `{10, 22, 35, 40, 45, 50, 80, 82, 85, 90, 100}` and search element `85`:
```
Element found at index: 8
```