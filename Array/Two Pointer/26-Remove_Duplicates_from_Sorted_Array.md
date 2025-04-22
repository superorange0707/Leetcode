# [26 - Remove Duplicates from Sorted Array]

🔗 [LeetCode Link](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

---

## Problem Description

>Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in nums.

Consider the number of unique elements of nums to be k, to get accepted, you need to do the following things:

Change the array nums such that the first k elements of nums contain the unique elements in the order they were present in nums initially. The remaining elements of nums are not important as well as the size of nums.
Return k.

---

## Idea

> use two pointer so we  only need to iterate once

---

## Logic

1. set slow pointer to mark current index
2. set fast pointer and use it for iterating
3. use fast pointer to find identical element
4. move the slow pointer then set the slow pointer = faster pointer 
---

## Code (Java - Closed Interval)

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int slow = 0;

        for(int fast = 0; fast <= nums.length - 1; fast++){
            if(nums[fast] != nums[slow]){
                nums[++slow] = nums[fast];
            }
        }

        // return slow;
        return slow + 1; //return first k element not the index

    }
}
```