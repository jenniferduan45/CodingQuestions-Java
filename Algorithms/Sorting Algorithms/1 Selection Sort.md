## Selection Sort
Given an array of integers, sort the elements in the array in ascending order. The selection sort algorithm should be used to solve this problem.

Examples
<br>{1} is sorted to {1}
<br>{1, 2, 3} is sorted to {1, 2, 3}
<br>{3, 2, 1} is sorted to {1, 2, 3}
<br>{4, 2, -3, 6, 1} is sorted to {-3, 1, 2, 4, 6}

Corner Cases
<br>What if the given array is null? In this case, we do not need to do anything.
<br>What if the given array is of length zero? In this case, we do not need to do anything.

### Code
```java
public int[] selectionSort(int[] array) {
  if (array == null || array.length == 0) return array;
  for (int i = 0; i < array.length; i++) {
    int minIndex = i;
    for (int j = i + 1; j < array.length; j++) {
      if (array[j] < array[minIndex]) {
        minIndex = j;
      }
    }
    int temp = array[i];
    array[i] = array[minIndex];
    array[minIndex] = temp;
  }
  return array;
}
```

### Complexity
- Time Complexity: O(n^2)
- Space Complexity: O(1)
