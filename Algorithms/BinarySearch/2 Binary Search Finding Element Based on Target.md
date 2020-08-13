# Binary Search Finding Element Based on Target
## 2.1 Closest Element to Target
Given a target integer T and an integer array A sorted in ascending order, find the index i in A such that A[i] is closest to T.

Assumptions
<br>There can be duplicate elements in the array, and we can return any of the indices with same value.

Examples
<br>A = {1, 2, 3}, T = 2, return 1
<br>A = {1, 4, 6}, T = 3, return 1
<br>A = {1, 4, 6}, T = 5, return 1 or 2
<br>A = {1, 3, 3, 4}, T = 2, return 0 or 1 or 2

Corner Cases
<br>What if A is null or A is of zero length? We should return -1 in this case.

### Analysis
- Implement binary search iteratively and reduce the search space to two elements left
- Compare which one is closer to target and return the closest one

### Code
```java
public int closest(int[] array, int target) {
  if (array == null || array.length == 0) return -1;
  int left = 0;
  int right = array.length - 1;
  while (left < right - 1) {
    int middle = left + (right - left) / 2;
    if (target == array[middle]) {
      return middle;
    } else if (target < array[middle]) {
      right = middle;
    } else {
      left = middle;
    }
  }
  if (target - array[left] <= array[right] - target) {
    return left;
  } else {
    return right;
  }
}
```
