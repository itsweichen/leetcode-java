## Jump Game

> Given an array of non-negative integers, you are initially positioned at the first index of the array.
>
> Each element in the array represents your maximum jump length at that position.
>
> Determine if you are able to reach the last index.

### Solution

尝试每种方法的话需要 $O(n^n)$ exponential 的时间。

能不能用DP呢？

下面是一种简化的DP。

```java
class Solution {
    public boolean canJump(int[] nums) {
        if (nums.length == 1) {
            return true; // !!
        }
        
        int maxReach = 0;
        for (int i = 0; i < nums.length - 1; i++) {
            if (maxReach < i) { // !!
                return false;
            }
            
            if (i + nums[i] > maxReach) {
                maxReach = i + nums[i];
            }
            if (maxReach >= nums.length - 1) {
                return true;
            }
        }
        return false;
    }
}
```

