# 🔢 Sorting Algorithms — The Complete Guide

> **Master every sorting algorithm** from fundamentals to advanced, with time complexity, code implementations, visual traces, interview Q&A, and real-world use cases.

---

## 📌 Table of Contents

1. [Why Learn Sorting Algorithms?](#-why-learn-sorting-algorithms)
2. [Big-O Cheat Sheet](#-big-o-complexity-cheat-sheet)
3. [Sorting Algorithms Overview](#-sorting-algorithms-overview)
4. [Bubble Sort](#1-bubble-sort)
5. [Selection Sort](#2-selection-sort)
6. [Insertion Sort](#3-insertion-sort)
7. [Merge Sort](#4-merge-sort)
8. [Quick Sort](#5-quick-sort)
9. [Heap Sort](#6-heap-sort)
10. [Counting Sort](#7-counting-sort)
11. [Radix Sort](#8-radix-sort)
12. [Bucket Sort](#9-bucket-sort)
13. [Shell Sort](#10-shell-sort)
14. [Tim Sort](#11-tim-sort)
15. [Interview Questions & Answers](#-interview-questions--answers)
16. [Choosing the Right Algorithm](#-when-to-use-which-algorithm)
17. [Common Mistakes to Avoid](#-common-mistakes-to-avoid)
18. [Practice Problems](#-practice-problems)
19. [Resources](#-resources)

---

## 🎯 Why Learn Sorting Algorithms?

Sorting is one of the **most fundamental operations in computer science**. It is:

- The backbone of databases, file systems, and search engines
- A gateway to understanding **time complexity** and **space complexity**
- One of the **most commonly asked topics in technical interviews** (Google, Amazon, Meta, Microsoft)
- A foundation for more advanced algorithms like binary search, divide-and-conquer, and tree operations

> 💡 **Fun Fact:** Over 25% of all CPU cycles in early computers were spent on sorting data.

---

## 📊 Big-O Complexity Cheat Sheet

| Algorithm      | Best Case   | Average Case | Worst Case  | Space      | Stable? | In-Place? |
|----------------|-------------|--------------|-------------|------------|---------|-----------|
| Bubble Sort    | O(n)        | O(n²)        | O(n²)       | O(1)       | ✅ Yes  | ✅ Yes    |
| Selection Sort | O(n²)       | O(n²)        | O(n²)       | O(1)       | ❌ No   | ✅ Yes    |
| Insertion Sort | O(n)        | O(n²)        | O(n²)       | O(1)       | ✅ Yes  | ✅ Yes    |
| Merge Sort     | O(n log n)  | O(n log n)   | O(n log n)  | O(n)       | ✅ Yes  | ❌ No     |
| Quick Sort     | O(n log n)  | O(n log n)   | O(n²)       | O(log n)   | ❌ No   | ✅ Yes    |
| Heap Sort      | O(n log n)  | O(n log n)   | O(n log n)  | O(1)       | ❌ No   | ✅ Yes    |
| Counting Sort  | O(n + k)    | O(n + k)     | O(n + k)    | O(k)       | ✅ Yes  | ❌ No     |
| Radix Sort     | O(nk)       | O(nk)        | O(nk)       | O(n + k)   | ✅ Yes  | ❌ No     |
| Bucket Sort    | O(n + k)    | O(n + k)     | O(n²)       | O(n + k)   | ✅ Yes  | ❌ No     |
| Shell Sort     | O(n log n)  | O(n log² n)  | O(n²)       | O(1)       | ❌ No   | ✅ Yes    |
| Tim Sort       | O(n)        | O(n log n)   | O(n log n)  | O(n)       | ✅ Yes  | ❌ No     |

> **Stable Sort**: Equal elements maintain their original relative order.  
> **In-Place**: Uses O(1) extra memory (no auxiliary arrays).

---

## 🗂️ Sorting Algorithms Overview

```
Sorting Algorithms
├── Comparison-Based          ← Compare elements to decide order
│   ├── Bubble Sort           O(n²)      — Simple, educational
│   ├── Selection Sort        O(n²)      — Minimal swaps
│   ├── Insertion Sort        O(n²)      — Great for nearly-sorted data
│   ├── Merge Sort            O(n log n) — Guaranteed, stable
│   ├── Quick Sort            O(n log n) — Fast in practice
│   ├── Heap Sort             O(n log n) — Optimal worst case
│   └── Shell Sort            O(n log²n) — Improved insertion sort
│
└── Non-Comparison-Based      ← Exploit structure of data
    ├── Counting Sort         O(n + k)   — Integer keys only
    ├── Radix Sort            O(nk)      — Fixed-length integers/strings
    └── Bucket Sort           O(n + k)   — Uniformly distributed floats
```

---

## 1. 🫧 Bubble Sort

### What is it?
Bubble Sort repeatedly compares **adjacent elements** and swaps them if they are in the wrong order. After each full pass, the **largest unsorted element "bubbles up"** to its correct position.

### How it Works (Step-by-Step)

```
Array: [5, 3, 8, 1, 2]

Pass 1:
  [5, 3, 8, 1, 2]  → Compare 5,3  → Swap → [3, 5, 8, 1, 2]
  [3, 5, 8, 1, 2]  → Compare 5,8  → OK  → [3, 5, 8, 1, 2]
  [3, 5, 8, 1, 2]  → Compare 8,1  → Swap → [3, 5, 1, 8, 2]
  [3, 5, 1, 8, 2]  → Compare 8,2  → Swap → [3, 5, 1, 2, 8] ← 8 in place ✅

Pass 2:
  [3, 5, 1, 2, 8]  → Compare 3,5  → OK
  [3, 5, 1, 2, 8]  → Compare 5,1  → Swap → [3, 1, 5, 2, 8]
  [3, 1, 5, 2, 8]  → Compare 5,2  → Swap → [3, 1, 2, 5, 8] ← 5 in place ✅

... continues until sorted
Final: [1, 2, 3, 5, 8] ✅
```

### Python Implementation

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        swapped = False
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        if not swapped:          # Optimization: stop early if already sorted
            break
    return arr

# Example
print(bubble_sort([64, 34, 25, 12, 22, 11, 90]))
# Output: [11, 12, 22, 25, 34, 64, 90]
```

### Java Implementation

```java
public static void bubbleSort(int[] arr) {
    int n = arr.length;
    for (int i = 0; i < n - 1; i++) {
        boolean swapped = false;
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                swapped = true;
            }
        }
        if (!swapped) break; // Already sorted
    }
}
```

### Key Properties
- **Best Case O(n)**: When array is already sorted (with the `swapped` optimization)
- **Worst Case O(n²)**: Reversed array
- **Stable**: Yes — equal elements are never swapped
- **Use Case**: Only for learning purposes; avoid in production

---

## 2. 🎯 Selection Sort

### What is it?
Selection Sort divides the array into a sorted and unsorted region. In each pass, it **selects the minimum element** from the unsorted region and places it at the end of the sorted region.

### How it Works (Step-by-Step)

```
Array: [64, 25, 12, 22, 11]

Pass 1: Find min in [64,25,12,22,11] → 11 → Swap with index 0
        [11, 25, 12, 22, 64]  ← 11 in place ✅

Pass 2: Find min in [25,12,22,64] → 12 → Swap with index 1
        [11, 12, 25, 22, 64]  ← 12 in place ✅

Pass 3: Find min in [25,22,64] → 22 → Swap with index 2
        [11, 12, 22, 25, 64]  ← 22 in place ✅

Pass 4: Find min in [25,64] → 25 → No swap needed
        [11, 12, 22, 25, 64]  ← sorted ✅
```

### Python Implementation

```python
def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        min_idx = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
    return arr

print(selection_sort([64, 25, 12, 22, 11]))
# Output: [11, 12, 22, 25, 64]
```

### Key Properties
- **Always O(n²)**: Regardless of input — no early termination
- **Minimum Swaps**: Only O(n) swaps — useful when write operations are expensive (e.g., flash memory)
- **Not Stable**: Swapping can change relative order of equal elements
- **Use Case**: When memory writes are expensive and input size is small

---

## 3. 🃏 Insertion Sort

### What is it?
Insertion Sort builds the sorted array **one element at a time**, like sorting playing cards in your hand. Each new element is "inserted" into its correct position within the already-sorted portion.

### How it Works (Step-by-Step)

```
Array: [5, 2, 4, 6, 1, 3]

Start: [5]  ← trivially sorted

Step 1: Insert 2 → [2, 5]
Step 2: Insert 4 → [2, 4, 5]
Step 3: Insert 6 → [2, 4, 5, 6]
Step 4: Insert 1 → [1, 2, 4, 5, 6]
Step 5: Insert 3 → [1, 2, 3, 4, 5, 6] ✅
```

### Python Implementation

```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]  # Shift elements right
            j -= 1
        arr[j + 1] = key         # Place key in correct position
    return arr

print(insertion_sort([12, 11, 13, 5, 6]))
# Output: [5, 6, 11, 12, 13]
```

### Key Properties
- **Best Case O(n)**: Already sorted — only one comparison per element
- **Adaptive**: Efficient for nearly-sorted data
- **Online Algorithm**: Can sort a list as it receives new elements
- **Stable**: Yes
- **Use Case**: Small arrays, nearly sorted data, online/streaming data

---

## 4. 🔀 Merge Sort

### What is it?
Merge Sort is a classic **divide-and-conquer** algorithm. It splits the array in half recursively until individual elements remain, then **merges** the halves back together in sorted order.

### How it Works (Step-by-Step)

```
Array: [38, 27, 43, 3, 9, 82, 10]

DIVIDE:
[38, 27, 43, 3, 9, 82, 10]
    ↙               ↘
[38, 27, 43]     [3, 9, 82, 10]
   ↙    ↘           ↙       ↘
[38]  [27,43]    [3,9]    [82,10]
       ↙  ↘      ↙  ↘     ↙   ↘
      [27][43]  [3] [9] [82]  [10]

MERGE:
[27][43] → [27, 43]
[3][9]   → [3, 9]
[82][10] → [10, 82]

[38][27,43] → [27, 38, 43]
[3,9][10,82] → [3, 9, 10, 82]

[27,38,43][3,9,10,82] → [3, 9, 10, 27, 38, 43, 82] ✅
```

### Python Implementation

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])

    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0

    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1

    result.extend(left[i:])
    result.extend(right[j:])
    return result

print(merge_sort([38, 27, 43, 3, 9, 82, 10]))
# Output: [3, 9, 10, 27, 38, 43, 82]
```

### Java Implementation

```java
public static void mergeSort(int[] arr, int left, int right) {
    if (left < right) {
        int mid = (left + right) / 2;
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }
}

public static void merge(int[] arr, int left, int mid, int right) {
    int n1 = mid - left + 1, n2 = right - mid;
    int[] L = new int[n1], R = new int[n2];
    for (int i = 0; i < n1; i++) L[i] = arr[left + i];
    for (int j = 0; j < n2; j++) R[j] = arr[mid + 1 + j];

    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        arr[k++] = (L[i] <= R[j]) ? L[i++] : R[j++];
    }
    while (i < n1) arr[k++] = L[i++];
    while (j < n2) arr[k++] = R[j++];
}
```

### Key Properties
- **Guaranteed O(n log n)**: Always, regardless of input
- **Stable**: Yes — maintains order of equal elements
- **Space O(n)**: Needs auxiliary array
- **Use Case**: Linked lists (no random access needed), external sorting (files too large for RAM), when stability is required

---

## 5. ⚡ Quick Sort

### What is it?
Quick Sort picks a **pivot** element, partitions the array such that elements less than the pivot go left and greater go right, then recursively sorts each partition. It is the **fastest sorting algorithm in practice** for average cases.

### How it Works (Step-by-Step)

```
Array: [3, 6, 8, 10, 1, 2, 1]    Pivot = last element (1)

Partition:
  Elements < 1:  []
  Pivot:         [1]
  Elements >= 1: [3, 6, 8, 10, 2, 1]

After one partition:
  [1, 1, 3, 6, 8, 10, 2]   (conceptual)

Recursively sort left [] and right [3,6,8,10,2,1]...
Final: [1, 1, 2, 3, 6, 8, 10] ✅
```

### Python Implementation

```python
def quick_sort(arr, low=0, high=None):
    if high is None:
        high = len(arr) - 1
    if low < high:
        pi = partition(arr, low, high)
        quick_sort(arr, low, pi - 1)
        quick_sort(arr, pi + 1, high)
    return arr

def partition(arr, low, high):
    pivot = arr[high]
    i = low - 1
    for j in range(low, high):
        if arr[j] <= pivot:
            i += 1
            arr[i], arr[j] = arr[j], arr[i]
    arr[i + 1], arr[high] = arr[high], arr[i + 1]
    return i + 1

arr = [10, 7, 8, 9, 1, 5]
print(quick_sort(arr))
# Output: [1, 5, 7, 8, 9, 10]
```

### Pivot Strategies

| Strategy      | Description                            | Pros/Cons                            |
|---------------|----------------------------------------|--------------------------------------|
| Last element  | `pivot = arr[high]`                    | Simple; O(n²) on sorted arrays       |
| First element | `pivot = arr[low]`                     | Simple; O(n²) on sorted arrays       |
| Random        | `pivot = arr[random(low, high)]`       | Avoids worst case most of the time   |
| Median-of-3   | Median of first, middle, last          | Best practical choice                |

### Key Properties
- **Average O(n log n)**, **Worst O(n²)** (rare with random pivot)
- **Not Stable**: Partition can reorder equal elements
- **Cache-Friendly**: In-place; better memory locality than Merge Sort
- **Use Case**: General-purpose sorting, large datasets, arrays (not linked lists)

---

## 6. 🏔️ Heap Sort

### What is it?
Heap Sort uses a **binary heap** data structure. It first builds a **Max-Heap** from the array, then repeatedly extracts the maximum element and places it at the end.

### Understanding a Max-Heap

```
Array: [4, 10, 3, 5, 1]

Max-Heap Tree:
          10
         /  \
        5    3
       / \
      4   1

Array representation: [10, 5, 3, 4, 1]
Parent of index i → (i-1)//2
Left child of i  → 2i+1
Right child of i → 2i+2
```

### Python Implementation

```python
def heap_sort(arr):
    n = len(arr)

    # Build Max-Heap (bottom-up)
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)

    # Extract elements one by one
    for i in range(n - 1, 0, -1):
        arr[0], arr[i] = arr[i], arr[0]   # Move max to end
        heapify(arr, i, 0)                 # Restore heap property

    return arr

def heapify(arr, n, i):
    largest = i
    left, right = 2 * i + 1, 2 * i + 2

    if left < n and arr[left] > arr[largest]:
        largest = left
    if right < n and arr[right] > arr[largest]:
        largest = right

    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, n, largest)

print(heap_sort([12, 11, 13, 5, 6, 7]))
# Output: [5, 6, 7, 11, 12, 13]
```

### Key Properties
- **Always O(n log n)**: Guaranteed best, average, and worst
- **Not Stable**: Heap operations can change relative order
- **Space O(1)**: In-place — no extra memory needed
- **Use Case**: When guaranteed worst-case O(n log n) is needed with O(1) space (e.g., embedded systems)

---

## 7. 🔢 Counting Sort

### What is it?
Counting Sort is a **non-comparison-based** algorithm. It works by **counting the frequency** of each distinct element, then placing elements in their correct positions. Works only for **integers within a known, limited range**.

### How it Works (Step-by-Step)

```
Array: [1, 4, 1, 2, 7, 5, 2]    Range: 0–7

Step 1 — Count:
  Index:  0  1  2  3  4  5  6  7
  Count: [0, 2, 2, 0, 1, 1, 0, 1]

Step 2 — Cumulative Count:
  Count: [0, 2, 4, 4, 5, 6, 6, 7]

Step 3 — Place elements (right to left for stability):
  Output: [1, 1, 2, 2, 4, 5, 7] ✅
```

### Python Implementation

```python
def counting_sort(arr):
    if not arr:
        return arr

    max_val = max(arr)
    count = [0] * (max_val + 1)

    for num in arr:
        count[num] += 1

    # Rebuild sorted array
    result = []
    for i, c in enumerate(count):
        result.extend([i] * c)

    return result

print(counting_sort([4, 2, 2, 8, 3, 3, 1]))
# Output: [1, 2, 2, 3, 3, 4, 8]
```

### Key Properties
- **O(n + k)** where k = range of values
- **Not in-place**: Requires extra O(k) space
- **Stable**: Yes (when implemented carefully)
- **Use Case**: Sorting ages, grades, exam scores, characters — any integer with limited range

---

## 8. 📻 Radix Sort

### What is it?
Radix Sort sorts numbers **digit by digit**, from the least significant digit (LSD) to the most significant digit (MSD), using Counting Sort as a subroutine for each digit position.

### How it Works (Step-by-Step)

```
Array: [170, 45, 75, 90, 802, 24, 2, 66]

Pass 1 — Sort by UNITS digit:
  170, 90, 802, 2 | 24 | 45, 75 | 66
  → [170, 90, 802, 2, 24, 45, 75, 66]

Pass 2 — Sort by TENS digit:
  802, 2 | 24 | 45 | 66 | 170, 75 | 90
  → [802, 2, 24, 45, 66, 170, 75, 90]

Pass 3 — Sort by HUNDREDS digit:
  2, 24, 45, 66, 75, 90 | 170 | 802
  → [2, 24, 45, 66, 75, 90, 170, 802] ✅
```

### Python Implementation

```python
def radix_sort(arr):
    max_val = max(arr)
    exp = 1
    while max_val // exp > 0:
        counting_sort_by_digit(arr, exp)
        exp *= 10
    return arr

def counting_sort_by_digit(arr, exp):
    n = len(arr)
    output = [0] * n
    count = [0] * 10

    for i in arr:
        index = (i // exp) % 10
        count[index] += 1

    for i in range(1, 10):
        count[i] += count[i - 1]

    for i in range(n - 1, -1, -1):
        index = (arr[i] // exp) % 10
        output[count[index] - 1] = arr[i]
        count[index] -= 1

    for i in range(n):
        arr[i] = output[i]

print(radix_sort([170, 45, 75, 90, 802, 24, 2, 66]))
# Output: [2, 24, 45, 66, 75, 90, 170, 802]
```

### Key Properties
- **O(nk)** where k = number of digits
- **Stable**: Yes
- **Use Case**: Sorting integers, fixed-length strings (like IP addresses, phone numbers), large datasets of integers

---

## 9. 🪣 Bucket Sort

### What is it?
Bucket Sort distributes elements into **buckets** (sub-arrays), sorts each bucket individually (often with Insertion Sort), then concatenates all buckets. Works best for **uniformly distributed floating-point numbers** in a known range.

### How it Works (Step-by-Step)

```
Array: [0.78, 0.17, 0.39, 0.26, 0.72, 0.94, 0.21, 0.12, 0.23, 0.68]
Buckets: 10 buckets for range [0.0, 1.0)

Bucket 0 [0.0–0.1): []
Bucket 1 [0.1–0.2): [0.17, 0.12]
Bucket 2 [0.2–0.3): [0.26, 0.21, 0.23]
Bucket 3 [0.3–0.4): [0.39]
...
Bucket 9 [0.9–1.0): [0.94]

Sort each bucket:
Bucket 1: [0.12, 0.17]
Bucket 2: [0.21, 0.23, 0.26]
...

Concatenate:
[0.12, 0.17, 0.21, 0.23, 0.26, 0.39, 0.68, 0.72, 0.78, 0.94] ✅
```

### Python Implementation

```python
def bucket_sort(arr):
    n = len(arr)
    if n == 0:
        return arr

    buckets = [[] for _ in range(n)]

    for num in arr:
        index = int(num * n)
        index = min(index, n - 1)
        buckets[index].append(num)

    for bucket in buckets:
        bucket.sort()

    return [num for bucket in buckets for num in bucket]

print(bucket_sort([0.78, 0.17, 0.39, 0.26, 0.72, 0.94, 0.21]))
# Output: [0.17, 0.21, 0.26, 0.39, 0.72, 0.78, 0.94]
```

### Key Properties
- **Average O(n + k)**; **Worst O(n²)** when all elements fall in one bucket
- **Stable**: Yes (if inner sort is stable)
- **Use Case**: Floating-point numbers, uniformly distributed data, GPA/scores in a fixed range

---

## 10. 🐚 Shell Sort

### What is it?
Shell Sort is an **improvement over Insertion Sort**. Instead of comparing only adjacent elements, it compares elements that are **far apart** using a "gap" sequence. The gap decreases with each pass until it becomes 1 (a final pass of Insertion Sort).

### How it Works (Step-by-Step)

```
Array: [12, 34, 54, 2, 3]    Gap = n//2 = 2

Pass 1 (gap=2): Compare arr[i] with arr[i-2]
  Compare 54, 12 → OK
  Compare 2, 34  → Swap → [12, 2, 54, 34, 3]
  Compare 3, 54  → Swap → [12, 2, 3, 34, 54]
  Array: [12, 2, 3, 34, 54]

Pass 2 (gap=1): Regular Insertion Sort
  Final: [2, 3, 12, 34, 54] ✅
```

### Python Implementation

```python
def shell_sort(arr):
    n = len(arr)
    gap = n // 2

    while gap > 0:
        for i in range(gap, n):
            temp = arr[i]
            j = i
            while j >= gap and arr[j - gap] > temp:
                arr[j] = arr[j - gap]
                j -= gap
            arr[j] = temp
        gap //= 2

    return arr

print(shell_sort([12, 34, 54, 2, 3]))
# Output: [2, 3, 12, 34, 54]
```

### Key Properties
- **O(n log² n)** average with Knuth's gap sequence
- **Not Stable**
- **In-Place**: Yes
- **Use Case**: Medium-sized arrays, embedded systems without recursion support

---

## 11. 🏆 Tim Sort

### What is it?
Tim Sort is a **hybrid sorting algorithm** derived from Merge Sort and Insertion Sort. It is the **default sorting algorithm in Python** (`sorted()` / `list.sort()`) and **Java** (`Arrays.sort()` for objects). It excels at sorting **real-world data** that often contains partially sorted sequences (called "runs").

### How it Works

```
1. Divide array into small "runs" (size 32–64)
2. Sort each run with Insertion Sort (fast for small arrays)
3. Merge runs using a modified Merge Sort with:
   - Galloping mode: skips ahead when one side is clearly dominant
   - Run detection: leverages natural ordering already in data

Array with natural runs:
[3, 7, 12, 1, 5, 9, 2, 8, 11, 4, 6, 10]
 ↑---------↑  ↑--------↑   ↑-----------↑
   Run 1         Run 2          Run 3
```

### Python Note

```python
# Python's built-in sort IS TimSort — already optimal!
arr = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
arr.sort()          # In-place TimSort
print(sorted(arr))  # Returns new sorted list
```

### Key Properties
- **O(n) Best Case**: Detects already-sorted sequences
- **O(n log n) Worst Case**: Guaranteed
- **Stable**: Yes
- **Use Case**: Real-world data, production environments, default choice in Python/Java

---

## 🎤 Interview Questions & Answers

### 🔹 Conceptual Questions

---

**Q1: What is a stable sorting algorithm? Give examples.**

> A stable sort preserves the **relative order of equal elements**. If `A[i] == A[j]` and `i < j` before sorting, then `A[i]` still appears before `A[j]` after sorting.
>
> **Stable**: Merge Sort, Insertion Sort, Bubble Sort, Tim Sort, Counting Sort, Radix Sort  
> **Unstable**: Quick Sort, Heap Sort, Selection Sort
>
> **When stability matters**: Sorting a list of employees first by department, then by name — stability ensures the name order within each department is preserved.

---

**Q2: What is the best general-purpose sorting algorithm and why?**

> For general use: **Quick Sort** (average O(n log n), cache-friendly, in-place) or **Tim Sort** (best for real-world data with partial ordering). Quick Sort is preferred for primitive arrays; Tim Sort (or Merge Sort) for objects requiring stability.

---

**Q3: Why is Merge Sort preferred for linked lists over Quick Sort?**

> Linked lists don't support **random access** — finding the middle element and partitioning require O(n) traversal. Merge Sort naturally works by splitting at the middle node (found via slow/fast pointer), and merging two sorted linked lists is efficient. Quick Sort's partition step becomes O(n²) due to repeated traversals.

---

**Q4: When would you use Counting Sort instead of Comparison-based sorts?**

> When:
> - Elements are **non-negative integers**
> - The **range k is not much larger than n** (k = O(n))
> - Example: sorting exam scores (0–100), ages (0–120), ASCII characters
>
> Avoid when: range is huge (e.g., sorting 1,000 numbers ranging from 0 to 10⁹ — would need 10⁹ count array slots)

---

**Q5: What is the theoretical minimum number of comparisons needed to sort n elements?**

> By information-theoretic lower bound, any comparison-based sort requires **Ω(n log n)** comparisons in the worst case. This is derived from the fact that there are n! possible permutations, and each comparison eliminates at most half the remaining possibilities: ⌈log₂(n!)⌉ ≈ n log₂ n comparisons.

---

**Q6: Explain the difference between in-place and not-in-place sorting.**

> **In-place**: Uses O(1) extra memory. Sorts within the original array. Examples: Bubble, Selection, Insertion, Heap, Quick Sort.  
> **Not in-place (out-of-place)**: Uses additional memory (O(n) or more). Examples: Merge Sort, Counting Sort, Radix Sort.
>
> Trade-off: In-place saves memory but can be harder to make stable.

---

**Q7: Why does Quick Sort have O(n²) worst case and how can you avoid it?**

> Worst case occurs when the **pivot is always the smallest or largest element** (e.g., sorted array with last-element pivot). This leads to partitions of size 0 and n-1, giving T(n) = T(n-1) + O(n) = O(n²).
>
> Solutions:
> 1. **Random pivot**: Randomize pivot selection to make worst case extremely unlikely
> 2. **Median-of-three**: Use median of first, middle, last as pivot
> 3. **Introsort**: Switch to Heap Sort when recursion depth exceeds a threshold (used in C++ STL)

---

**Q8: How does Heap Sort achieve O(n log n) guaranteed?**

> A binary heap allows:
> - **Build Max-Heap**: O(n) — using bottom-up heapification
> - **Extract max n times**: Each extraction is O(log n) → total O(n log n)
>
> Since both steps are bounded, no pathological input can degrade performance.

---

**Q9: Can you sort in O(n) time? Under what conditions?**

> Yes, but only with **non-comparison-based** sorts:
> - **Counting Sort**: O(n + k) — integers in range [0, k]
> - **Radix Sort**: O(nk) — integers with k digits
> - **Bucket Sort**: O(n) expected — uniformly distributed floats
>
> These bypass the Ω(n log n) lower bound because they exploit properties of the data (not just comparisons).

---

**Q10: What is the space complexity of recursive Quick Sort and Merge Sort?**

> - **Quick Sort**: O(log n) average stack space (recursive calls). O(n) worst case if pivot always unbalanced.
> - **Merge Sort**: O(n) for the auxiliary array + O(log n) for the recursion stack = O(n) total.

---

### 🔹 Coding Questions

---

**Q11: Sort an array of 0s, 1s, and 2s without using a sorting function (Dutch National Flag Problem)**

```python
def sort_colors(arr):
    low, mid, high = 0, 0, len(arr) - 1
    while mid <= high:
        if arr[mid] == 0:
            arr[low], arr[mid] = arr[mid], arr[low]
            low += 1; mid += 1
        elif arr[mid] == 1:
            mid += 1
        else:
            arr[mid], arr[high] = arr[high], arr[mid]
            high -= 1
    return arr

print(sort_colors([2, 0, 2, 1, 1, 0]))  # [0, 0, 1, 1, 2, 2]
# Time: O(n), Space: O(1)
```

---

**Q12: Find the k-th largest element in an unsorted array.**

```python
import random

def kth_largest(arr, k):
    # Quick Select — Average O(n)
    k = len(arr) - k  # k-th largest = (n-k)-th smallest

    def quick_select(l, r):
        pivot = arr[r]
        p = l
        for i in range(l, r):
            if arr[i] <= pivot:
                arr[p], arr[i] = arr[i], arr[p]
                p += 1
        arr[p], arr[r] = arr[r], arr[p]

        if p < k:   return quick_select(p + 1, r)
        elif p > k: return quick_select(l, p - 1)
        else:       return arr[p]

    return quick_select(0, len(arr) - 1)

print(kth_largest([3, 2, 1, 5, 6, 4], k=2))  # 5
```

---

**Q13: Merge K sorted arrays.**

```python
import heapq

def merge_k_sorted(arrays):
    heap = []
    for i, arr in enumerate(arrays):
        if arr:
            heapq.heappush(heap, (arr[0], i, 0))

    result = []
    while heap:
        val, arr_idx, ele_idx = heapq.heappop(heap)
        result.append(val)
        if ele_idx + 1 < len(arrays[arr_idx]):
            next_val = arrays[arr_idx][ele_idx + 1]
            heapq.heappush(heap, (next_val, arr_idx, ele_idx + 1))

    return result
# Time: O(N log k) where N = total elements, k = number of arrays
```

---

**Q14: Sort a nearly-sorted (k-sorted) array where each element is at most k positions from its sorted position.**

```python
import heapq

def sort_k_sorted(arr, k):
    heap = arr[:k + 1]
    heapq.heapify(heap)

    result = []
    for i in range(k + 1, len(arr)):
        result.append(heapq.heappushpop(heap, arr[i]))

    while heap:
        result.append(heapq.heappop(heap))

    return result
# Time: O(n log k) — much better than O(n log n) when k << n
```

---

**Q15: Count inversions in an array (number of pairs where i < j but arr[i] > arr[j]).**

```python
def count_inversions(arr):
    if len(arr) <= 1:
        return arr, 0

    mid = len(arr) // 2
    left, left_inv = count_inversions(arr[:mid])
    right, right_inv = count_inversions(arr[mid:])

    merged = []
    inversions = left_inv + right_inv
    i = j = 0

    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            merged.append(left[i]); i += 1
        else:
            merged.append(right[j]); j += 1
            inversions += len(left) - i   # All remaining left elements form inversions

    merged.extend(left[i:])
    merged.extend(right[j:])
    return merged, inversions

_, inv = count_inversions([2, 4, 1, 3, 5])
print(inv)  # 3  (pairs: (2,1), (4,1), (4,3))
# Time: O(n log n)
```

---

## 📌 When to Use Which Algorithm

```
Is the data nearly sorted?
    YES → Insertion Sort (O(n) best case)
    NO  ↓

Are elements integers in a small range?
    YES → Counting Sort or Radix Sort (O(n + k))
    NO  ↓

Is stability required?
    YES → Merge Sort or Tim Sort
    NO  ↓

Is memory a constraint (need O(1) space)?
    YES + guaranteed O(n log n) → Heap Sort
    YES + speed matters more    → Quick Sort (random pivot)
    NO  ↓

Default choice for large data?
    → Tim Sort (Python/Java) or Quick Sort with random pivot
```

| Scenario | Best Choice |
|---|---|
| Small array (n < 20) | Insertion Sort |
| Nearly sorted data | Insertion Sort or Tim Sort |
| Integer keys, small range | Counting Sort |
| Large integers or strings | Radix Sort |
| Stability required | Merge Sort / Tim Sort |
| Minimum memory, guaranteed performance | Heap Sort |
| Linked list | Merge Sort |
| General purpose (arrays) | Quick Sort / Tim Sort |
| External sorting (data on disk) | Merge Sort |
| Uniformly distributed floats | Bucket Sort |

---

## ⚠️ Common Mistakes to Avoid

1. **Using Bubble Sort in production** — It's O(n²); always use a better algorithm for real data.

2. **Forgetting Quick Sort's worst case** — Always use random pivot or median-of-three for untrusted input.

3. **Counting Sort with huge ranges** — If range k >> n (e.g., sorting 100 numbers in range 0 to 10⁹), use Radix Sort instead.

4. **Treating comparison sorts as faster than O(n log n) is possible** — They can't beat Ω(n log n) by information theory.

5. **Assuming Python's `sorted()` is always O(n log n)** — For nearly-sorted input, Tim Sort achieves O(n).

6. **Off-by-one errors in Quick Sort partition** — Carefully track whether `high` is inclusive or exclusive.

7. **Stack overflow in recursive Quick Sort** — For very large arrays, use iterative Quick Sort or limit recursion depth.

---

## 📝 Practice Problems

### Beginner
- [ ] Implement Bubble Sort and add the swapped-flag optimization
- [ ] Sort an array of strings alphabetically using Insertion Sort
- [ ] Find the maximum and minimum in an unsorted array

### Intermediate
- [ ] [LeetCode 75](https://leetcode.com/problems/sort-colors/) — Sort Colors (Dutch National Flag)
- [ ] [LeetCode 215](https://leetcode.com/problems/kth-largest-element-in-an-array/) — Kth Largest Element
- [ ] [LeetCode 912](https://leetcode.com/problems/sort-an-array/) — Sort an Array (implement from scratch)
- [ ] [LeetCode 56](https://leetcode.com/problems/merge-intervals/) — Merge Intervals
- [ ] Sort a linked list using Merge Sort

### Advanced
- [ ] [LeetCode 315](https://leetcode.com/problems/count-of-smaller-numbers-after-self/) — Count of Smaller Numbers After Self
- [ ] [LeetCode 493](https://leetcode.com/problems/reverse-pairs/) — Reverse Pairs (modified Merge Sort)
- [ ] [LeetCode 23](https://leetcode.com/problems/merge-k-sorted-lists/) — Merge K Sorted Lists
- [ ] Implement External Merge Sort for a file too large to fit in memory
- [ ] Implement Introsort (Quick Sort + Heap Sort hybrid, used in C++ STL)

---

## 📚 Resources

### 📖 Books
- *Introduction to Algorithms* (CLRS) — Chapters 6–8
- *The Algorithm Design Manual* — Steven Skiena
- *Algorithms* — Robert Sedgewick & Kevin Wayne

### 🌐 Online Resources
- [Visualgo — Sorting Visualizations](https://visualgo.net/en/sorting)
- [Big-O Cheat Sheet](https://www.bigocheatsheet.com/)
- [CS50 Sorting Lecture](https://cs50.harvard.edu/x/2024/weeks/3/)
- [Sorting Algorithms Animations — toptal](https://www.toptal.com/developers/sorting-algorithms)

### 🎥 Video Tutorials
- MIT OpenCourseWare — 6.006 Introduction to Algorithms
- Abdul Bari's Sorting Playlist (YouTube)
- NeetCode Sorting Problems (YouTube)

---

## 🤝 Contributing

Contributions are welcome! To add a new algorithm or improve existing implementations:

1. Fork the repository
2. Create a branch: `git checkout -b feature/algorithm-name`
3. Add your implementation with:
   - Clear comments explaining each step
   - Time and space complexity analysis
   - At least one test case
4. Submit a Pull Request

### Contribution Checklist
- [ ] Implementation is correct and tested
- [ ] Time and space complexity is documented
- [ ] Code follows the existing style
- [ ] README section added for the new algorithm

---

## 📜 License

This repository is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

<div align="center">

**⭐ Star this repo if it helped you crack your interview! ⭐**

Made with ❤️ for learners everywhere

</div>
