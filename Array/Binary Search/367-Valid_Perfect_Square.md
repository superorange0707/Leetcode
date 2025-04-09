# [367-Valid Perfect Square]

🔗 [LeetCode Link](https://leetcode.com/problems/valid-perfect-square)

---

## Problem Description

>Given a positive integer num, return true if num is a perfect square or false otherwise.

A perfect square is an integer that is the square of an integer. In other words, it is the product of some integer with itself.

You must not use any built-in library function, such as sqrt.

Constraints: 0 <= x <= 231 - 1

---

## Idea

> Since the array is sorted, binary search is the most efficient choice (O(log n)).

---

## Logic

1. Define your search range (0 - x)
2. Use a loop (`while (left <= right)` or `while (left < right)`)
3. Calculate mid, check if square(mid) == x
4. change to the boundary accordingly
5. Use (long) mid * mid to prevent integer overflow in large input cases (e.g. x = 2147395599)



---

## Code (Java - Closed Interval)

```java
class Solution {
    public boolean isPerfectSquare(int num) {
        // set search range
        int left = 0;
        int right = num;

        while(left <= right){
            int mid = left + (right - left)/2; 

            // to avoid int overflow
            long square =(long) mid * mid;

            if (square > num){
                right = mid - 1;
            }
            else if(square < num){
                left = mid + 1;
            }
            else{
                // can find root
                return true;
            }
        }
        return false;
        
    }
}


```