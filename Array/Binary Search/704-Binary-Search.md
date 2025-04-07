# [704 - Binary Search]

🔗 [LeetCode Link](https://leetcode.com/problems/binary-search/)

---

## Problem Description

>Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.


---

## Idea

> Since the array is sorted, binary search is the most efficient choice (O(log n)).

---

## Logic

1. check the edge cases
2. Define your search range
3. Use a loop (`while (left <= right)` or `while (left < right)`)
4. Calculate mid, check if target is found
5. change to the boundary accordingly



---

## Code (Java - Closed Interval)

```java
class Solution {
    public int search(int[] nums, int target) {
        // check edge case
        if(target > nums[nums.length - 1] || target < nums[0]){
            return -1;
        }

        // define search range
        int left = 0;
        int right = nums.length - 1;

        // use closed interval
        while (left <= right){
            int mid = left + (right-left)/2;

            // search the right boundary
            if (nums[mid] < target){
                left = mid + 1;
            }
            // search the left boundary
            else if(nums[mid] > target){
                right = mid - 1;
            }
            // target = nums[mid]
            else{
                return mid;
            }
        }
        
        return -1;

    }
}


```

## Code (Java - Half-Open Interval)

```java
class Solution {
    public int search(int[] nums, int target) {
        // check edge case
        if(target > nums[nums.length - 1] || target < nums[0]){
            return -1;
        }

        // define search range
        int left = 0;
        int right = nums.length;

        // use closed interval
        while (left < right){
            int mid = left + (right-left)/2;

            if (nums[mid] < target){
                left = mid + 1;
            }
            else if(nums[mid] > target){
                right = mid;
            }
            else{
                return mid;
            }
        }
        
        return -1;

    }
}
```