## Merge Sort
Given an array of integers, sort the elements in the array in ascending order. The merge sort algorithm should be used to solve this problem.

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
public int[] mergeSort(int[] array) {
  if (array == null || array.length <= 1) return array;
  return mergeSort(array, 0, array.length - 1);
}

public int[] mergeSort(int[] array, int left, int right) {
  if (left == right) {
    return new int[]{array[left]};
  }
  int middle = left + (right - left) / 2;
  int[] leftPart = mergeSort(array, left, middle);
  int[] rightPart = mergeSort(array, middle + 1, right);
  return merge(leftPart, rightPart);
}

public int[] merge(int[] one, int[] two) {
  int i = 0;
  int j = 0;
  int k = 0;
  int[] result = new int[one.length + two.length];
  while (i < one.length && j < two.length) {
    if (one[i] <= two[j]) {
      result[k] = one[i];
      k++;
      i++;
    } else {
      result[k] = two[j];
      k++;
      j++;
    }
  }
  while (i < one.length) {
    result[k] = one[i];
    k++;
    i++;
  }
  while (j < two.length) {
    result[k] = two[j];
    k++;
    j++;
  }
  return result;
}
```

### Complexity
- Time Complexity: O(n log n)
- Space Complexity: O(n)
