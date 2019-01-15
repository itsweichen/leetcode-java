## Maximum Subarray

> Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

### Solution

**Brute force**

- Time:  $O(n^2)$
- Space:  $O(1)$

**Dynamic Programming**

Let S(i-1) be the largest sum of the array A[0...i-1] containing the element A[i-1].

Then $S[i-1] = max(S[i-2] + A[i-1], A[i-1])$, and $S[0] = 0$, $S[1] = A[0]$.

```java
class Solution {
    public int maxSubArray(int[] nums) {
        if (nums.length == 0) {
            return 0;
        }
        
        int localSum = nums[0];
        int globalSum = nums[0]; // can't use 0!
        for(int i = 1; i < nums.length; i++) { // should start from 1
            localSum = localSum + nums[i] > nums[i] ? localSum + nums[i] : nums[i];
            globalSum = localSum > globalSum ? localSum : globalSum;
        }
        return globalSum;
    }
}
```

**Divide and Conquer???**

