# [35 -Search Insert Position]

🔗 [LeetCode Link](https://leetcode.com/problems/search-insert-position/)

---

## Problem Description

>Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.


---

## Idea

> Since the array is sorted, binary search is the most efficient choice (O(log n)).

---

## Logic

1. Define your search range
2. Use a loop (`while (left <= right)` or `while (left < right)`)
3. Calculate mid, check if target is found
4. change to the boundary accordingly



---

## Code (Java - Closed Interval)

```java
class Solution {
    public int searchInsert(int[] nums, int target) {

        int left = 0; int right = nums.length - 1;

        while(left <= right){
            int mid = left + ((right - left)/2);
            
            if(nums[mid] < target){
                left = mid + 1;
            }
            else if(nums[mid] > target){
                right = mid - 1;
            }
            else{
                return mid;
            }
        }
        return right+1;
        
    }
}


```

## Code (Java - Half-Open Interval)

```java
class Solution {
    public int searchInsert(int[] nums, int target) {

        int left = 0; int right = nums.length;

        while(left < right){
            int mid = left + ((right - left)/2);
            
            if(nums[mid] < target){
                left = mid + 1;
            }
            else if(nums[mid] > target){
                right = mid;
            }
            else{
                return mid;
            }
        }
        return right;
    }
}
```