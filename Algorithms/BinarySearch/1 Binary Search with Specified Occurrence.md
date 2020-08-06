# Binary Search with Specified Occurrence
## 1.1 First Occurrence
Given a target integer T and an integer array A sorted in ascending order, find the index of the first occurrence of T in A or return -1 if there is no such index.

Assumptions
<br>There can be duplicate elements in the array.

Examples
<br>A = {1, 2, 3}, T = 2, return 1
<br>A = {1, 2, 3}, T = 4, return -1
<br>A = {1, 2, 2, 2, 3}, T = 2, return 1

Corner Cases
<br>What if A is null or A of zero length? We should return -1 in this case.

### Analysis
- The general procedure is the same as classical binary search:
  - Determine search space 
  - Find middle index and compare
- Difference is the result after comparison:
  - If `target == array[middle]`, we should not return instantly as before. We should continue to check whether there are elements before `middle` index that are equal to `target`.
  - For other cases, things are the same as classical binary search
  - The most important thing is to make sure that the result is the first element that is equal to `target`
- Instead of leaving only one element in the end, we need to leave two elements to see which one is the first occurrence
  - If `target == array[left]`, then index `left` is the first occurrence
  - If `target == array[right]`, then index `right` is the first occurrence
  - If neither is equal to `target`, then return -1;

### Code
```java
public int firstOccur(int[] array, int target) {
  if (array == null || array.length == 0) return -1;
  int left = 0;
  int right = array.length - 1;
  while (left < right - 1) {
    int middle = left + (right - left)/ 2;
    if (target == array[middle]) {
      // Check elements before middle
      right = middle;
    } else if (target < array[middle]) {
      right = middle - 1;
    } else {
      left = middle + 1;
    }
  }
  // Post-processing
  if (target == array[left]) {
    return left;
  }
  if (target == array[right]) {
    return right;
  }
  return -1;
}
```

### Complexity
- Time complexity: O(log n)
- Space complexity: O(1)
---
## 1.2 Last Occurrence

### Analysis
- Almost the same as 1.1, except we should continue to check whether there are elements after `middle` index that are equal to `target`

### Code
```java
public int lastOccur(int[] array，int target) {
  if (array == null || array.length == 0) return -1;
  int left = 0;
  int right = array.length - 1;
  while (left < right - 1) {
    int middle = left + (right - left) / 2;
    if (target == array[middle]) {
      // Check elements after middle
      left = middle;
    } else if (target < array[middle]) {
      right = middle - 1;
    } else {
      left = middle + 1;
    }
  }
  //Post-processing
  if (target == array[right]) {
    return right;
  }
  if (target == array[left]) {
    return left;
  }
  return -1;
}
```

### Complexity
- Time complexity: O(log n)
- Space complexity: O(1)
