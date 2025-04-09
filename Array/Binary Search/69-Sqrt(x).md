# [69 - Sqrt(x)]

🔗 [LeetCode Link](https://leetcode.com/problems/sqrtx/)

---

## Problem Description

>Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well. Constraints: 0 <= x <= 231 - 1

---

## Idea

> binary search is efficient choice (O(log n)).

---

## Logic

1. Define your search range (0 - x)
2. Use a loop (`while (left <= right)` or `while (left < right)`)
3. Calculate mid, check if square(mid) == x
4. change to the boundary accordingly
5. 	•	Use a variable ans to store the best valid value seen so far (ans = mid when mid * mid <= x)
	•	This helps when the square root isn’t exact — we round down
6. Use (long) mid * mid to prevent integer overflow in large input cases (e.g. x = 2147395599)



---

## Code (Java - Closed Interval)

```java
class Solution {
    public int mySqrt(int x) {
        // set search range
        int left = 0;
        int right = x;
        int ans = -1;

        // improve effiency
        if (x<2){
            return x;
        }

        while(left <= right){
            int mid = left + ((right - left)/2);

            // use (long)mid * mid to avoid int overflow(int is 2^31 - 1 ) 
            if( (long)mid * mid > x){
                // move to left boundary
                right = mid -1;
            }
            else if ((long)mid * mid < x){

                // make the result will round to nearest
                ans = mid;

                // move to right boundary
                left = mid + 1;
            }
            else{
                return mid;
            }

        }
        return ans;
    }
}


```

## Code (Java - Half-Open Interval)

```java
class Solution {
    public int mySqrt(int x) {
        // set search range
        int left = 0;
        int right = x;

    // improve effiency
        if (x<2){
            return x;
        }

        while(left < right){
            int mid = left + ((right - left)/2);

            // use (long)mid * mid to avoid int overflow(int is 2^31 - 1 ) 
            if( (long)mid * mid > x){
                // move to left boundary
                right = mid;
            }
            else if ((long)mid * mid < x){
                // move to right boundary
                left = mid + 1;
            }
            else{
                return mid;
            }

        }

        // to round down
        return left - 1;
    }
}
```