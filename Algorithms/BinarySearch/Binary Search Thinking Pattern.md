# Binary Search Thinking Pattern
## Assumptions
- The array is sorted.

## General Method
- Two indices `left` and `right`, and area between `[left, right]` is the search space waited to be cheked.
- Index `middle = left + (right - left) / 2` is used to determine how to decrease the search space.
  - If `target == array[middle]`, return `middle`.
  - If `target < array[middle]`, then `right = middle - 1`.
  - If `target > array[middle]`, then `left = middle + 1`.

## Principles
- After each iteration, search space decreases.
- When the range of search space decreases, target (if exists) cannot be ruled out accidentally.

## Complexity
- Search space decreases by half -> consider log n
