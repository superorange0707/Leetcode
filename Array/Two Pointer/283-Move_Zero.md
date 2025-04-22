# [283 - Move Zero]

🔗 [LeetCode Link](https://leetcode.com/problems/move-zeroes/)

---

## Problem Description

>Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.

---

## Idea

> use two pointer so we  only need to iterate once

---

## Logic

1. set slow pointer to mark current index
2. set fast pointer and use it for iterating
3. use fast pointer to find non-zero element
4. swap the value between slow 


---

## Code (Java - Closed Interval)

```java
class Solution {
    public void moveZeroes(int[] nums) {

        // set slow pointer
        int slow = 0;
        
        // use fast pointer in the loop
        for(int fast = 0; fast <= nums.length - 1; fast++){

            // exchange value when fast pointer point to non-zero element
            if(nums[fast] != 0){
                int tmp = nums[slow];

                // move slow pointer
                nums[slow++] = nums[fast];
                nums[fast] = tmp;
            }
        }
    }
}
```