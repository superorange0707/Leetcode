# [34 - Find First and Last Position of Element in Sorted Array]

🔗 [LeetCode Link](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

---

## Problem Description

>Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.

---

## Idea

> Since the array is sorted, binary search is an efficient choice (O(log n)).

---

## Logic

1. Define your search range
2. Use a `while (left <= right)` loop to perform binary search.
3. To find the **first position**:
   - Since there might be multiple elements equal to the target, we need to locate the **first one**.
   - So whenever `nums[mid] >= target`, we move the **right boundary** to the left — even when `nums[mid] == target`.
   - This ensures we keep searching **from right to left** until we find the first match.
4. To find the **last position**:
   - Reset `left` and `right`, and repeat a similar binary search.
   - This time, when `nums[mid] <= target`, we move the **left boundary** to the right — even when `nums[mid] == target`.
   - This ensures we keep searching **from left to right** until we find the last match.



---

## Code (Java - Closed Interval)

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        // set result arry
        int[] res = new int[]{-1,-1};


        // set search range
        int left = 0;
        int right = nums.length - 1;


        //find the first position
        while(left <= right){
            int mid = left + (right - left)/2;

            // here may be multiple elements equal to target,  we need to find the first one
            // have to keep searching from right to left until the first element < target (if target founded)
            if(nums[mid] >= target){
                if(nums[mid] == target){
                    // record first postion index and keep updating it if multiple elements found
                    res[0] = mid;
                }
                right = mid - 1;
            } 

            // // If nums[mid] < target, discard left half
            else{
                left = mid + 1;
            }
        }



        // find the last position.
        left = 0;
        right = nums.length - 1;
        while (left <= right){
            int mid = left + (right - left)/2;

            // There may be multiple elements equal to target,
            // so we continue searching to the right to find the last one
            if(nums[mid] <= target){
                if(nums[mid] == target){
                    res[1] = mid;
                }
                left = mid + 1;
            }

            // If nums[mid] > target, discard right half
            else {
                right = mid -1;
            }
        }

        return res;
        
    }
}
```