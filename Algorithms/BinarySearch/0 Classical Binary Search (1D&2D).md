# Classical Binary Search Questions
## 0.1 1D Classical Binary Search
Given a target integer T and an integer array A sorted in ascending order, find the index i such that A[i] == T or return -1 if there is no such index.

Assumptions:
<br>There can be duplicate elements in the array, and you can return any of the indices i such that A[i] == T.

Examples:
<br>A = {1, 2, 3, 4, 5}, T = 3, return 2
<br>A = {1, 2, 3, 4, 5}, T = 6, return -1
<br>A = {1, 2, 2, 2, 3, 4}, T = 2, return 1 or 2 or 3

Corner Cases:
<br>What if A is null or A is of zero length? We should return -1 in this case.

### Code
```java
public int binarySearch(int[] array, int target) {
   if (array == null || array.length == 0 ) return -1;
   int left = 0;
   int right = array.length - 1;
   while (left <= right) {
        int middle = left + (right - left) / 2;
        if (target == array[middle]) {
            return middle;
        } else if (target < array[middle]) {
            right = middle - 1;
        } else {
            left = middle + 1;
        }
   }
   return -1;
}
```

### Complexity
- Time complexity: O(log n)
- Space complexity: O(1)
---
## 0.2 2D Classical Binary Search
Given a 2D matrix that contains integers only, which each row is sorted in an ascending order. The first element of next row is larger than (or equal to) the last element of previous row.

Given a target number, returning the position that the target locates within the matrix. If the target number does not exist in the matrix, return {-1, -1}.

Assumptions:
<br>The given matrix is not null, and has size of N * M, where N >= 0 and M >= 0.

Examples:
<br>matrix = { {1, 2, 3}, {4, 5, 7}, {8, 9, 10} }, target = 7, return {1, 2}
<br>target = 6, return {-1, -1} to represent the target number does not exist in the matrix.

### Analysis
- Streching the matrix into a 1D array row by row, our general method for binary search still holds.
- Mutual tranformation between matrix index and 1D array index:
   - Suppose matrix is {{a, b, c}, {d, e, f}, {g, h, i}}: for element c, its matrix index is {0, 2}. 
   - Transforming to 1D array, the array is {a, b, c, d, e, f, g, h, i}: for element c, its array index is 2.
   - Transformation rule: array index `i` -> matrix index `{i / matrix[0].length, i % matrix[0].length}`.

### Code
```java
public int[] matrixBinarySearch(int[][] matrix, int target) {
   int row = matrix.length;
   int column = matrix[0].length;
   int[] result = new int[]{-1, -1};
   if (row == 0 && column == 0) return result;
   int left = 0;
   int right = row * column - 1;
   while (left <= right) {
      int middle = left + (right - left) / 2;
      int rowIndex = middle / column;
      int columnIndex = middle % column;
      if (target == matrix[rowIndex][columnIndex]) {
         result[0] = rowIndex;
         result[1] = columnIndex;
         return result;
      } else if (target < matrix[rowIndex][columnIndex]) {
         right = middle - 1;
      } else {
         left = middle + 1;
      }
   }
   return result;
}
```

### Complexity
- Time complexity: O(log(m * n))
- Space complexity: O(1)
