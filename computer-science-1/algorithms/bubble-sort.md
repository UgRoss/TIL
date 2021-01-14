---
description: >-
  ℹ️ Sorting algorithm that compares every adjacent pair of values and swaps
  their position if the first value is greater than another. Complexity O(n²)
---

# Bubble Sort

### Description

The bubble sort algorithm runs in O\(n²\) time, making it an inefficient algorithm for a larger list.

The idea behind the bubble sort is that every adjacent pair of values is repeatedly compared, and then these values swap their positions if the first value is greater than the second value. This way during each pass through the array, the largest value “bubbles up” to the top.

### Example

Let's imagine that we need to sort the following array using bubble sorting: `[7, 1, 4, 3, 8]`. Here is the list of the steps that bubble sorting will do to sort this array:

1. \[**7**, **1**, 4, 3, 8\] -&gt; \[**1**, **7**, 4, 3, 8\]
2. \[1, **7**, **4**, 3, 8\] -&gt; \[1, **4**, **7**, 3, 8\]
3. \[1, 4, **7**, **3**, 8\] -&gt; \[1, 4, **3**, **7**, 8\]
4. \[1, 4, 3, **7**, **8**\] -&gt; \[1, 4, 3, **7**, **8**\]

Second pass:

1. \[**1**, **4**, 3, 7, 8\] -&gt; \[**1**, **4**, 3, 7, 8\]
2. \[1, **4**, **3**, 7, 8\] -&gt; \[1, **3**, **4**, 7, 8\]
3. \[1, 3, **4**, **7**, 8\] -&gt; \[1, 3, **4**, **7**, 8\]
4. \[1, 3, 4, **7**, **8**\] -&gt; \[1, 3, 4, **7**, **8**\]

Now, our array is already sorted, but the algorithm doesn't know about it. The algorithm still needs one whole pass to end its sorting.

Third pass:

1. \[**1**, **4**, 3, 7, 8\] -&gt; \[**1**, **4**, 3, 7, 8\]
2. \[1, **3**, **4**, 7, 8\] -&gt; \[1, **3**, **4**, 7, 8\]
3. \[1, 3, **4**, **7**, 8\] -&gt; \[1, 3, **4**, **7**, 8\]
4. \[1, 3, 4, **7**, **8**\] -&gt; \[1, 3, 4, **7**, **8**\]

### Code implementation

Here is one of the possible ways to implement bubble sorting:

```javascript
function bubbleSort(inputArr) {
  const arr = [...inputArr];

  for (let i = 0; i < arr.length - 1; i++) {
    for (let j = 0; j < arr.length - 1 - i; j++) {
      if (arr[j] > arr[j + 1]) {
        // ⬇ Swap two elements using Destruturing assignment
        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
      }
    }
  }

  return arr;
}
```

Even if an array is sorted the function always runs O\(n²\) time. It can be optimized if the inner loop didn't make any swap during its execution.

```javascript
function bubbleSort(inputArr) {
  const arr = [...inputArr];
  let swapped = false;

  for (let i = 0; i < arr.length - 1; i++) {
    swapped = false;
    for (let j = 0; j < arr.length - 1 - i; j++) {
      if (arr[j] > arr[j + 1]) {
        // ⬇ Swap two elements using Destruturing assignment
        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
        swapped = true;
      }
    }

    // Break our loop if during inner loop execution there was no swaps
    if (!swapped) {
      break;
    }
  }

  return arr;
}
```

This time if our `inputArr` is already sorted complexity will be O\(n\).

### **Complexity**

1. **Worst and Avg. Time Complexity:** _**O\(n²\)**_
2. **Best Case Time Complexity:** _**O\(n\)**_. Happens only when an array is already sorted.

