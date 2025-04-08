# Binary Search

Binary search is a powerful technique used to find elements in a **sorted array** in **O(log n)** time.  
It works by repeatedly dividing the search interval in half. The key to implementing it correctly is understanding the **interval type** and consistently applying the correct logic.

---

## Interval Types

### Closed Interval `[left, right]` -> right = array.size - 1

- Loop condition: `while (left <= right)`
- Update rules:
  - If `nums[mid] < target`: move `left = mid + 1`
  - If `nums[mid] > target`: move `right = mid - 1`
- This approach ensures all elements between `left` and `right` (inclusive) are considered.

### Half-Open Interval `[left, right)`  -> right = array.size

- Loop condition: `while (left < right)`
- Update rules:
  - If `nums[mid] < target`: move `left = mid + 1`
  - If `nums[mid] > target`: move `right = mid`
- `right` is exclusive, so we must **never access `nums[right]`**.

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

| #    | Title         | Link                                           | Difficulty |
| ---- | ------------- | ---------------------------------------------- | ---------- |
| 704  | Binary Search | [704-Binary-Search.md](./704-Binary-Search.md) | Easy       |
| 35  | Search Insert Position | [35-Search_Insert_Position.md](./35-Search_Insert_Position.md) | Easy       |
| 69  | Sqrt(x) | [69-Sqrt(x).md](./69-Sqrt(x).md) | Easy       |