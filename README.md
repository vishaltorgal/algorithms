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
