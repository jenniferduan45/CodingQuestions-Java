## Quick Sort
Given an array of integers, sort the elements in the array in ascending order. The quick sort algorithm should be used to solve this problem.

Examples
<br>{1} is sorted to {1}
<br>{1, 2, 3} is sorted to {1, 2, 3}
<br>{3, 2, 1} is sorted to {1, 2, 3}
<br>{4, 2, -3, 6, 1} is sorted to {-3, 1, 2, 4, 6}

Corner Cases
<br>What if the given array is null? In this case, we do not need to do anything.
<br>What if the given array is of length zero? In this case, we do not need to do anything.

### Analysis
- 挡板思想: `i` and `j` as two indices partition the array into three sections
  - `[left range, i)` represents elements smaller than the pivot
  - `[i, j]` represents all elements waited to be processed
  - `(j, right range]`represents elements largen than the pivot

### Code
```java
public int[] quickSort(int[] array) {
  if (array == null || array.length <= 1) {
    return array;
  }
  quickSort(array, 0, array.length - 1);
  return array;
}

public void quickSort(int[] array, int left, int right) {
  if (left >= right) return;
  int pivotPos = partition(array, left, right);
  quickSort(array, left, pivotPos - 1);
  quickSort(array, pivotPos + 1, right);
}

public int partition(int[] array, int one, int two) {
  int pivotNum = pivotIndex(one, two);
  int pivot = array[pivotNum];
  swap(array, pivotNum, two);
  int i = 0;
  int j = two - 1;
  while (i <= j) {
    if (array[i] <= pivot) {
      i ++;
    } else if (array[i] > pivot) {
      swap(array, i, j);
      j --;
    }
  }
  swap(array, i, two);
  return i;
}

public void swap(int[] array, int a, int b) {
  int temp = array[a];
  array[a] = array[b];
  array[b] = temp;
}

private int pivotIndex(int left, int right) {
  return left + (int) (Math.random() * (right - left + 1));
}
```

### Complexity
- Time Complexity: worst case O(n^2), average O(n log n)
- Space Complexity: O(1)
