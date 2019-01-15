## Search Insert Position

> Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
>
> You may assume no duplicates in the array.

### Solution

```java
// 17.45%

class Solution {
    public int searchInsert(int[] nums, int target) {
        // Solution 1: linear time
        // Solution 2: binary search - O(logn)
        int left = 0;
        int right = nums.length; // cannot be nums.length - 1
        // failed at [1,3,5,6], 7 (output: 4)
        
        while (left < right) {
            int mid = (left + right) / 2;
            if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        
        return right;
    }
}
```

