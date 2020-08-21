# Longest Increasing Subarray & Subsequence Problems
## 1.1 Longest Ascending Subarray
Given an unsorted array, find the length of the longest subarray in which the numbers are in ascending order.

Assumptions
<br>The given array is not null

Examples
<br>{7, 2, 3, 1, 5, 8, 9, 6}, longest ascending subarray is {1, 5, 8, 9}, length is 4.
<br>{1, 2, 3, 3, 4, 4, 5}, longest ascending subarray is {1, 2, 3}, length is 3.

### Analysis
- High level: using DP
- Details:
  - Use `count[i]` to store the length of the longest ascending subarray from 0-th element to i-th element
  - Base case: `count[0] = 1` 
  - Induction rule: if `array[j] > array[j - 1]`, then `count[j] = count[j - 1] + 1`; else, `count[j] = 1`
  - Update `maxNum`, the global maximum length of ascending subarray, when `count[j] > maxNum`

### Code
```java
public int longest(int[] array) {
  if (array.length == 0) return 0;
  int[] count = new int[array.length];
  count[0] = 1;
  int maxNum = count[0];
  for (int i = 1; i < array.length; i ++) {
    if (array[i] > array[i - 1]) {
      count[i] = count[i - 1] + 1;
    } else {
      count[i] = 1;
    }
    maxNum = Math.max(maxNum, count[i]);
  }
  return maxNum;
}
```

### Complexity
- Time Complexity: O(n)
- Space Complexity: O(n)
---
## 1.2 Longest Ascending Subsequence

---
## 1.3* Print an Arbitrary Longest Ascending Subsequence

---
## 1.4 Count the Number of Ascending Subsequences

---
## 1.5 Largest Subset of Points in Which Any Pair of Points Can Form a Line With Positive Slope
