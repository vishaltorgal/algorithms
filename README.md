# Algorithms (2025–2026)

### Table of Contents
1. [Linear Search](#1-linear-search)
2. [Binary Search](#2-binary-search)
3. [Bubble Sort](#3-bubble-sort)
4. [Merge Sort](#4-merge-sort)
5. [Quick Sort](#5-quick-sort)
6. [Two Pointers](#6-two-pointers)
7. [Sliding Window](#7-sliding-window)
8. [Prefix Sum](#8-prefix-sum)
9. [Hashing](#9-hashing)
10. [Recursion](#10-recursion)
11. [Greedy Algorithm](#11-greedy-algorithm)
12. [Backtracking](#12-backtracking)
13. [Dynamic Programming](#13-dynamic-programming)
14. [Breadth First Search](#14-breadth-first-search)
15. [Depth First Search](#15-depth-first-search)



## 1. **Linear Search**
Check each element one by one until you find the target.

***Example***
```jsx
const arr = [5, 10, 20, 30];
const target = 20;

for (let i = 0; i < arr.length; i++) {
  if (arr[i] === target) {
    console.log("Found at index", i);
    break;
  }
}
```
***Time Complexity***
- O(n)

***Explanation***
- In the worst case, the element is at the end or not present
- So we check n elements

***Space Complexity***
- O(1)

***Explanation***
- We only use a few variables
- No extra memory grows with input size
  
<br>

## 2. **Binary Search**
Binary search finds an element by dividing the search space in half each time.

Array must be sorted

<img width="1010" height="448" alt="image" src="https://github.com/user-attachments/assets/082ab5de-4011-4b2a-910e-7b2fd729c9f8" />

***Example***
```jsx
const arr = [5, 10, 20, 30, 40];
const target = 20;
```

***Binary Search code***
```jsx
let left = 0;
let right = arr.length - 1;

while (left <= right) {
  const mid = Math.floor((left + right) / 2);

  if (arr[mid] === target) {
    console.log("Found at index", mid);
    break;
  } else if (arr[mid] < target) {
    left = mid + 1;
  } else {
    right = mid - 1;
  }
}
```

***Time Complexity***
- O(log n)

***Explanation***
- Each step cuts the array into half.


***Space Complexity***
- O(1)

***Explanation***
- Uses only few variables.

***Best case***
- Target is exactly in middle
- Time O(1)

***Worst case***
- Keep dividing until one element left
- Time O(log n)

## 3. **Bubble Sort**

Bubble sort repeatedly compares adjacent elements and swaps them if they are in the wrong order.
Bigger values slowly bubble to the end.

<img width="150" height="217" alt="image" src="https://github.com/user-attachments/assets/6d916425-78eb-4596-b15d-9cad002f4915" />

***Bubble Sort code***
```jsx
const arr = [5, 4, 3, 2, 1];

for (let i = 0; i < arr.length; i++) {
console.log("==============");
  for (let j = 0; j < arr.length - i - 1; j++) {
    if (arr[j] > arr[j + 1]) {
      // swap
      let temp = arr[j];
      arr[j] = arr[j + 1];
      arr[j + 1] = temp;
    }
  console.log(arr);
  }
}

console.log(arr);
//[ 1, 2, 3, 4, 5 ]
```
***Console - How it works***
```jsx
==============
[ 4, 5, 3, 2, 1 ]
[ 4, 3, 5, 2, 1 ]
[ 4, 3, 2, 5, 1 ]
[ 4, 3, 2, 1, 5 ]
==============
[ 3, 4, 2, 1, 5 ]
[ 3, 2, 4, 1, 5 ]
[ 3, 2, 1, 4, 5 ]
==============
[ 2, 3, 1, 4, 5 ]
[ 2, 1, 3, 4, 5 ]
==============
[ 1, 2, 3, 4, 5 ]
==============
[ 1, 2, 3, 4, 5 ]
```

***Time Complexity***
- Best case
- O(n) (already sorted, with optimization)

- Average case
- O(n²)

- Worst case
- O(n²)

***Space Complexity***
- O(1)
- Sorting happens in place

## 4. **Merge Sort**

The ***Merge Sort*** algorithm is a divide-and-conquer algorithm that sorts an array by first breaking it down into smaller arrays, and then building the array back together.

<img width="244" height="236" alt="image" src="https://github.com/user-attachments/assets/3af48292-8bed-4603-b5a8-495828842a3f" />

```jsx
function mergeSort(arr) {
  if (arr.length <= 1) return arr;

  const mid = Math.floor(arr.length / 2);
  const left = arr.slice(0, mid);
  const right = arr.slice(mid);

  return merge(mergeSort(left), mergeSort(right));
}

function merge(left, right) {
  let result = [];
  let i = 0;
  let j = 0;

  while (i < left.length && j < right.length) {
    if (left[i] < right[j]) {
      result.push(left[i]);
      i++;
    } else {
      result.push(right[j]);
      j++;
    }
  }

  while (i < left.length) {
    result.push(left[i]);
    i++;
  }

  while (j < right.length) {
    result.push(right[j]);
    j++;
  }

  return result;
}

// Example
console.log(mergeSort([4,2,1,3]));
//[ 1, 2, 3, 4 ]
```

***Visual summary 1***
```jsx
[4,2,1,3]
   ↓
[4,2]   [1,3]
 ↓  ↓    ↓  ↓
[4][2]  [1][3]

Merge back →
[2,4]   [1,3]
      ↓
[1,2,3,4]
```
***Visual summary 2***
```jsx
mergeSort([4,2,1,3])
 ├─ mergeSort([4,2])  → [2,4]
 ├─ mergeSort([1,3])  → [1,3]
 └─ merge([2,4], [1,3]) → [1,2,3,4]

```
***Visual summary 3***
```jsx
mergeSort([4,2,1,3])
 ├─ mergeSort([4,2])
 │   ├─ mergeSort([4])
 │   │   → return [4]
 │   └─ mergeSort([2])
 │       → return [2]
 │   → merge([4], [2]) = [2,4]
 │
 └─ mergeSort([1,3])
     ├─ mergeSort([1])
     │   → return [1]
     └─ mergeSort([3])
         → return [3]
     → merge([1], [3]) = [1,3]

 → merge([2,4], [1,3]) = [1,2,3,4]

```

***Time Complexity***

- Best case
- O(n log n)

- Average case
- O(n log n)

- Worst case
- O(n log n)

- Very reliable.

***Space Complexity***

- O(n)
  
- Needs extra space for merging.
