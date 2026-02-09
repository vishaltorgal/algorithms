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
