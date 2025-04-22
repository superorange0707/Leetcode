# [27 - Remove Element]

🔗 [LeetCode Link](https://leetcode.com/problems/remove-element/)

---

## Problem Description

>Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.

Consider the number of elements in nums which are not equal to val be k, to get accepted, you need to do the following things:

Change the array nums such that the first k elements of nums contain the elements which are not equal to val. The remaining elements of nums are not important as well as the size of nums.
Return k.

---

## Idea

> use two pointer so we  only need to iterate once

---

## Logic

1. set slow pointer to mark current index
2. set fast pointer and use it for iterating
3. use fast pointer to find non-target element
4. set the slow pointer = faster pointer then move the slow pointer


---

## Code (Java - Closed Interval)

```java
class Solution {
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
}
```