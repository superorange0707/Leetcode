# Binary Search

Two Pointers is a versatile technique used to solve problems involving arrays or strings, especially when working with sorted data, windows, or in-place operations.
It uses two indices that move towards or across the data to find solutions efficiently in O(n) time.

---

## Fast & Slow Pointers (slow = 0, fast = 1)

- Used for removing duplicates, cycle detection, in-place updates
- use fast for exploring, slow is used to update
- Template

```java
    public int removeElement(int[] nums, int val) {

        // set the slow pointer
        int slow = 0;

        // set  the faster pointer
        for(int fast = 0; fast <= nums.length -1;fast++){
            // we use the fast pointer to check values, and make sure the fist slow number elements are not equal to val
            if(nums[fast] != val){
                nums[slow++] = nums[fast];
            }
        }
        return slow;
    }


```

## Opposite Ends( left = 0, right = array.length - 1)

- Used when array is sorted
-	Typical for sum problems, palindrome checks, merging
-	Move pointers inward based on condition
- Template


```java



```


---

## Tips

- The array must be **sorted** and preferably **contain no duplicates**.
- Use `mid = left + (right - left) // 2` to avoid integer overflow.
- Always consider edge cases:
  - Empty array
  - Only one element
  - All elements the same (duplicates)

---

## Common Patterns

### Closed Interval `[left, right]`

| Pattern        | Loop Type               | Conditions                                 |
| -------------- | ----------------------- | ------------------------------------------ |
| Standard       | `while (left <= right)` | `if nums[mid] == target`: return `mid`     |
| Left Boundary  | `while (left <= right)` | `if nums[mid] > target`: `right = mid - 1` |
| Right Boundary | `while (left <= right)` | `if nums[mid] < target`: `left = mid + 1`  |

---

### Half-Open Interval `[left, right)`

| Pattern        | Loop Type              | Conditions                                |
| -------------- | ---------------------- | ----------------------------------------- |
| Standard       | `while (left < right)` | `if nums[mid] == target`: return `mid`    |
| Left Boundary  | `while (left < right)` | `if nums[mid] > target`: `right = mid`    |
| Right Boundary | `while (left < right)` | `if nums[mid] < target`: `left = mid + 1` |

---

## Problems

| #   | Title                               | Link                                                         | Difficulty |
| --- | ----------------------------------- | ------------------------------------------------------------ | ---------- |
| 26  | Remove Duplicates from Sorted Array | [26-Remove_Duplicates_from_Sorted_Array.md](./26-Remove_Duplicates_from_Sorted_Array.md) | Easy       |
| 27  | Remove Element                      | [27-Remove_Element.md](./27-Remove_Element.md)               | Easy       |
| 283 | Move Zero                           | [283-Move_Zero.md](./283-Move_Zero.md)                       | Easy       |
