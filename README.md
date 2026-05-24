# Sorting Algorithms 🚀

Welcome to the **Sorting Algorithms** tutorial repository! This comprehensive guide covers the fundamental concepts of sorting, basic definitions, Java implementations, and algorithmic performance tracking for 10 essential sorting techniques.

---

## 📚 Table of Contents
1. [What is Sorting?](#-what-is-sorting)
2. [Sorting Basics & Core Concepts](#-sorting-basics--core-concepts)
3. [Classification of Sorting Techniques](#-classification-of-sorting-techniques)
4. [Sorting Algorithms Implementation](#-sorting-algorithms-implementation)
   * [1. Bubble Sort](#1-bubble-sort)
   * [2. Insertion Sort](#2-insertion-sort)
   * [3. Selection Sort](#3-selection-sort)
   * [4. Merge Sort](#4-merge-sort)
   * [5. Quick Sort](#5-quick-sort)
   * [6. Heap Sort](#6-heap-sort)
   * [7. Shell Sort](#7-shell-sort)
   * [8. Counting Sort](#8-counting-sort)
   * [9. Radix Sort](#9-radix-sort)
   * [10. Bucket Sort](#10-bucket-sort)
5. [Complexity Analysis Summary Matrix](#-complexity-analysis-summary-matrix)

---

## 🔍 What is Sorting?
**Sorting** refers to the rearrangement of a given array or list of elements according to a comparison operator. The comparison operator determines the new sequential order of elements within the data structure (e.g., ascending or descending order).

---

## 🧠 Sorting Basics & Core Concepts

* **In-place Sorting:** An in-place sorting algorithm uses constant extra space, meaning it modifies the original array directly without requiring extra memory proportional to the input size. 
    * *Examples:* Selection Sort, Bubble Sort, Insertion Sort, Heap Sort.
* **Internal Sorting:** Occurs when all data fits entirely within the system's main memory (RAM). The input size is strictly constrained by the allocated memory limit.
* **External Sorting:** Used when the dataset is too massive to fit into the main memory at once. Data is loaded in chunks from external storage (like a hard drive).
    * *Example:* Merge Sort is heavily utilized in external sorting.
* **Stable Sorting:** A sorting algorithm is stable if it preserves the relative order of duplicate elements from the original un-sorted array.
    * *Examples:* Merge Sort, Insertion Sort, Bubble Sort.
* **Hybrid Sorting:** An algorithm that combines two or more standard sorting techniques to maximize performance efficiency across different data sizes.
    * *Example:* **IntroSort** (combines Quick Sort, Heap Sort, and Insertion Sort) or **TimSort** (Merge Sort + Insertion Sort).

---

## 🛠 Classification of Sorting Techniques

| Category | Description | Examples |
| :--- | :--- | :--- |
| **Comparison-based** | Algorithms that determine the order by explicitly comparing elements against one another. | Bubble Sort, Quick Sort, Merge Sort |
| **Non-comparison-based** | Algorithms that use the mathematical properties or distribution of keys instead of direct comparisons. | Counting Sort, Radix Sort, Bucket Sort |

---

## 💻 Sorting Algorithms Implementation

### 1. Bubble Sort
Repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The largest unsorted element "bubbles up" to its correct position at the end of the array after each pass.

```java
class GFG {
    static void bubbleSort(int arr[], int n) {
        int i, j, temp;
        boolean swapped;
        for (i = 0; i < n - 1; i++) {
            swapped = false;
            for (j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swapped = true;
                }
            }
            if (swapped == false)
                break;
        }
    }

    public static void main(String args[]) {
        int arr[] = { 5, 6, 1, 3 };
        int n = arr.length;
        bubbleSort(arr, n);
        for (int i = 0; i < n; i++)
            System.out.print(arr[i] + " ");
    }
}
Input Array: [5, 6, 1, 3]Expected Output: 1 3 5 6 2. Insertion SortBuilds the sorted array one item at a time. It works just like sorting playing cards in your hand; each newly picked card is systematically shifted left into its correct position relative to the cards already sorted.Javapublic


2. Insertion Sort
Builds the sorted array one item at a time. It works just like sorting playing cards in your hand; each newly picked card is systematically shifted left into its correct position relative to the cards already sorted.


class GfG {
    static void insertionSort(int arr[]) {
        int n = arr.length;
        for (int i = 1; i < n; ++i) {
            int key = arr[i];
            int j = i - 1;

            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j = j - 1;
            }
            arr[j + 1] = key;
        }
    }

    public static void main(String args[]) {
        int arr[] = { 12, 11, 13, 5, 6 };
        insertionSort(arr);
        for (int i = 0; i < arr.length; ++i)
            System.out.print(arr[i] + " ");
    }
}
Input Array: [12, 11, 13, 5, 6]Expected Output: 5 6 11 12 13 3. Selection SortDivides the array into a sorted segment and an unsorted segment. It continuously scans the unsorted segment to find the absolute minimum value, and swaps it directly with the first element of the unsorted segment.


3. Selection Sort
Divides the array into a sorted segment and an unsorted segment. It continuously scans the unsorted segment to find the absolute minimum value, and swaps it directly with the first element of the unsorted segment.



import java.util.Arrays;

class GfG {
    static void selectionSort(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            int min_idx = i;
            for (int j = i + 1; j < n; j++) {
                if (arr[j] < arr[min_idx]) {
                    min_idx = j;
                }
            }
            int temp = arr[i];
            arr[i] = arr[min_idx];
            arr[min_idx] = temp;           
        }
    }

    public static void main(String[] args) {
        int[] arr = { 64, 25, 12, 22, 11 };
        selectionSort(arr);
        for (int val : arr) {
            System.out.print(val + " ");
        }
    }
}
Input Array: [64, 25, 12, 22, 11]Expected Output: 11 12 22 25 64 4. Merge SortA highly efficient, stable, and predictable algorithm that leverages a Divide and Conquer paradigm. It structurally splits the data structure into halves, handles them individually, and stitches them back together seamlessly.


3. Selection Sort
Divides the array into a sorted segment and an unsorted segment. It continuously scans the unsorted segment to find the absolute minimum value, and swaps it directly with the first element of the unsorted segment.


import java.io.*;

class GfG {
    static void merge(int arr[], int l, int m, int r) {
        int n1 = m - l + 1;
        int n2 = r - m;

        int L[] = new int[n1];
        int R[] = new int[n2];

        for (int i = 0; i < n1; ++i)
            L[i] = arr[l + i];
        for (int j = 0; j < n2; ++j)
            R[j] = arr[m + 1 + j];

        int i = 0, j = 0;
        int k = l;
        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k] = L[i];
                i++;
            } else {
                arr[k] = R[j];
                j++;
            }
            k++;
        }

        while (i < n1) {
            arr[k] = L[i];
            i++;
            k++;
        }

        while (j < n2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }

    static void mergeSort(int arr[], int l, int r) {
        if (l < r) {
            int m = l + (r - l) / 2;
            mergeSort(arr, l, m);
            mergeSort(arr, m + 1, r);
            merge(arr, l, m, r);
        }
    }

    public static void main(String args[]) {
        int arr[] = {38, 27, 43, 10};
        mergeSort(arr, 0, arr.length - 1);
        int n = arr.length;
        for (int i = 0; i < n; ++i)
            System.out.print(arr[i] + " ");
        System.out.println();
    }
}
Input Array: [38, 27, 43, 10]Expected Output: 10 27 38 43 5. Quick SortA divide-and-conquer strategy that picks an element as a pivot and partitions the elements around it, sorting the smaller elements to the left and greater ones to the right, before recursively tackling the sub-segments.

4. Merge Sort
A highly efficient, stable, and predictable algorithm that leverages a Divide and Conquer paradigm. It structurally splits the data structure into halves, handles them individually, and stitches them back together seamlessly.






import java.util.Arrays;

class GfG {
    static int partition(int[] arr, int low, int high) {
        int pivot = arr[high];
        int i = low - 1;

        for (int j = low; j <= high - 1; j++) {
            if (arr[j] < pivot) {
                i++;
                swap(arr, i, j);
            }
        }
        swap(arr, i + 1, high);  
        return i + 1;
    }

    static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

    static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int pi = partition(arr, low, high);
            quickSort(arr, low, pi - 1);
            quickSort(arr, pi + 1, high);
        }
    }

    public static void main(String[] args) {
        int[] arr = {10, 7, 8, 9, 1, 5};
        int n = arr.length;
        quickSort(arr, 0, n - 1);
        for (int val : arr) {
            System.out.print(val + " ");  
        }
    }
}
Input Array: [10, 7, 8, 9, 1, 5]Expected Output: 1 5 7 8 9 10 6. Heap SortAn optimized extension of Selection Sort that makes use of a Binary Heap data structure. Utilizing a max-heap allows instant reference access to the largest item, keeping operations quick and memory bound to in-place boundaries.


5. Quick Sort
A divide-and-conquer strategy that picks an element as a pivot and partitions the elements around it, sorting the smaller elements to the left and greater ones to the right, before recursively tackling the sub-segments.



import java.util.Arrays;

public class GFG {
    static void heapify(int[] arr, int n, int i) {
        int largest = i;
        int l = 2 * i + 1;
        int r = 2 * i + 2;

        if (l < n && arr[l] > arr[largest])
            largest = l;

        if (r < n && arr[r] > arr[largest])
            largest = r;

        if (largest != i) {
            int temp = arr[i];
            arr[i] = arr[largest];
            arr[largest] = temp;

            heapify(arr, n, largest);
        }
    }

    static void heapSort(int[] arr) {
        int n = arr.length;

        for (int i = n / 2 - 1; i >= 0; i--)
            heapify(arr, n, i);

        for (int i = n - 1; i > 0; i--) {
            int temp = arr[0];
            arr[0] = arr[i];
            arr[i] = temp;

            heapify(arr, i, 0);
        }
    }

    public static void main(String[] args) {
        int[] arr = { 9, 4, 3, 8, 10, 2, 5 };
        heapSort(arr);
        for (int i = 0; i < arr.length; ++i)
            System.out.print(arr[i] + " ");
    }
}
Input Array: [9, 4, 3, 8, 10, 2, 5]Expected Output: 2 3 4 5 8 9 10 7. Shell SortAn explicit variant of insertion sort designed to break down long-distance data dependencies. It starts by comparing items far away from each other over a shifting structured sequence gap, reducing comparison cycles down the line.


6. Heap Sort
An optimized extension of Selection Sort that makes use of a Binary Heap data structure. Utilizing a max-heap allows instant reference access to the largest item, keeping operations quick and memory bound to in-place boundaries.


public class GFG {
    public static void shellSort(int[] arr) {
        int n = arr.length;

        for (int gap = n / 2; gap > 0; gap /= 2) {
            for (int i = gap; i < n; i++) {
                int temp = arr[i]; 
                int j = i;

                while (j >= gap && arr[j - gap] > temp) {
                    arr[j] = arr[j - gap];
                    j -= gap;
                }
                arr[j] = temp;
            }
        }
    }

    public static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        int[] arr = {12, 34, 54, 2, 3};
        shellSort(arr);
        printArray(arr);
    }
}
Input Array: [12, 34, 54, 2, 3]Expected Output: 2 3 12 34 54 8. Counting SortA non-comparison linear integer sort model that tracks array keys based on direct mapping occurrences into index counting arrays. Highly specialized and optimally swift when value domains are small.

7. Shell Sort
An explicit variant of insertion sort designed to break down long-distance data dependencies. It starts by comparing items far away from each other over a shifting structured sequence gap, reducing comparison cycles down the line.





import java.util.Arrays;

public class CountingSort {
    public static int[] countSort(int[] arr) {
        int n = arr.length;
        if (n == 0) {
            return new int[0];
        }

        int maxVal = arr[0];
        for (int i = 1; i < n; i++) {
            if (arr[i] > maxVal) {
                maxVal = arr[i];
            }
        }

        int[] cntArr = new int[maxVal + 1];
        for (int i = 0; i <= maxVal; i++) {
            cntArr[i] = 0;
        }

        for (int i = 0; i < n; i++) {
            cntArr[arr[i]]++;
        }

        for (int i = 1; i <= maxVal; i++) {
            cntArr[i] += cntArr[i - 1];
        }

        int[] ans = new int[n];
        for (int i = n - 1; i >= 0; i--) {
            int v = arr[i];
            ans[cntArr[v] - 1] = v;
            cntArr[v]--;
        }

        return ans;
    }

    public static void main(String[] args) {
        int[] arr = {2, 5, 3, 0, 2, 3, 0, 3};
        int[] ans = countSort(arr);
        System.out.println(Arrays.toString(ans));
    }
}
Input Array: [2, 5, 3, 0, 2, 3, 0, 3]Expected Output: [0, 0, 2, 2, 3, 3, 3, 5]9. Radix SortProcesses digit segments piece by piece, from Least Significant Digit (LSD) up towards the Most Significant Digit (MSD). It scales without direct pairwise element value checks by applying localized stable count distributions sequentially.


8. Counting Sort
A non-comparison linear integer sort model that tracks array keys based on direct mapping occurrences into index counting arrays. Highly specialized and optimally swift when value domains are small.






import java.io.*;
import java.util.*;

class Radix {
    static int getMax(int arr[], int n) {
        int mx = arr[0];
        for (int i = 1; i < n; i++)
            if (arr[i] > mx)
                mx = arr[i];
        return mx;
    }

    static void countSort(int arr[], int n, int exp) {
        int output[] = new int[n]; 
        int i;
        int count[] = new int[10];
        Arrays.fill(count, 0);

        for (i = 0; i < n; i++)
            count[(arr[i] / exp) % 10]++;

        for (i = 1; i < 10; i++)
            count[i] += count[i - 1];

        for (i = n - 1; i >= 0; i--) {
            output[count[(arr[i] / exp) % 10] - 1] = arr[i];
            count[(arr[i] / exp) % 10]--;
        }

        for (i = 0; i < n; i++)
            arr[i] = output[i];
    }

    static void radixsort(int arr[], int n) {
        int m = getMax(arr, n);
        for (int exp = 1; m / exp > 0; exp *= 10)
            countSort(arr, n, exp);
    }

    static void print(int arr[], int n) {
        for (int i = 0; i < n; i++)
            System.out.print(arr[i] + " ");
    }

    public static void main(String[] args) {
        int arr[] = { 170, 45, 75, 90, 802, 24, 2, 66 };
        int n = arr.length;
        radixsort(arr, n);
        print(arr, n);
    }
}
Input Array: [170, 45, 75, 90, 802, 24, 2, 66]Expected Output: 2 24 45 66 75 90 170 802 10. Bucket SortDistributes targets over a series of dynamically calculated isolated lists or fractional buckets. Once mapped out, individual sub-buckets sort their own components cleanly via an Insertion Sort engine before sequential collection concatenation.

9. Radix Sort
Processes digit segments piece by piece, from Least Significant Digit (LSD) up towards the Most Significant Digit (MSD). It scales without direct pairwise element value checks by applying localized stable count distributions sequentially.


import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void insertionSort(List<Float> bucket) {
        for (int i = 1; i < bucket.size(); ++i) {
            float key = bucket.get(i);
            int j = i - 1;
            while (j >= 0 && bucket.get(j) > key) {
                bucket.set(j + 1, bucket.get(j));
                j--;
            }
            bucket.set(j + 1, key);
        }
    }


10. Bucket Sort
Distributes targets over a series of dynamically calculated isolated lists or fractional buckets. Once mapped out, individual sub-buckets sort their own components cleanly via an Insertion Sort engine before sequential collection concatenation.

    public static void bucketSort(float[] arr) {
        int n = arr.length;

        List<Float>[] buckets = new ArrayList[n];
        for (int i = 0; i < n; i++) {
            buckets[i] = new ArrayList<>();
        }

        for (int i = 0; i < n; i++) {
            int bi = (int) (n * arr[i]);
            buckets[bi].add(arr[i]);
        }

        for (int i = 0; i < n; i++) {
            insertionSort(buckets[i]);
        }

        int index = 0;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < buckets[i].size(); j++) {
                arr[index++] = buckets[i].get(j);
            }
        }
    }

    public static void main(String[] args) {
        float[] arr = {0.897f, 0.565f, 0.656f, 0.1234f, 0.665f, 0.3434f};
        bucketSort(arr);
        System.out.println("Sorted array is:");
        for (float num : arr) {
            System.out.print(num + " ");
        }
    }
}
Input Array: [0.897f, 0.565f, 0.656f, 0.1234f, 0.665f, 0.3434f]Expected Output: 0.1234 0.3434 0.565 0.656 0.665 0.897 📊 Complexity Analysis Summary MatrixAlgorithm NameBest CaseAverage CaseWorst CaseSpace ComplexityStable?Method Paradigm UsedQuick Sort$O(n \log n)$$O(n \log n)$$O(n^2)$$O(\log n)$❌ NoPartitioningMerge Sort$O(n \log n)$$O(n \log n)$$O(n \log n)$$O(n)$YesMergingHeap Sort$O(n \log n)$$O(n \log n)$$O(n \log n)$$O(1)$❌ NoSelection Heap TreeInsertion Sort$O(n)$$O(n^2)$$O(n^2)$$O(1)$YesInsertion ShiftsTim Sort$O(n)$$O(n \log n)$$O(n \log n)$$O(n)$YesInsertion & Merging RunSelection Sort$O(n^2)$$O(n^2)$$O(n^2)$$O(1)$❌ NoSelection ScansShell Sort$O(n \log n)$$O(n^{4/3})$$O(n^{3/2})$$O(1)$❌ NoGapped Insertion ShiftsBubble Sort$O(n)$$O(n^2)$$O(n^2)$$O(1)$YesNeighbor ExchangingCycle Sort$O(n^2)$
