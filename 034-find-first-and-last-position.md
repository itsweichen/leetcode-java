## Find First and Last Position of Element in Sorted Array

> Given an array of integers `nums` sorted in ascending order, find the starting and ending position of a given `target` value.
>
> Your algorithm's runtime complexity must be in the order of *O*(log *n*).
>
> If the target is not found in the array, return `[-1, -1]`.

### Solution

对于 sorted array 找东西，显然用 Binary Search 呀。

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        
        int lowerBound, upperBound, mid;
        
        int l = 0;
        int r = nums.length;
        // l - first element that is >= target
        while (l < r) {
            mid = (l + r) / 2;
            if (nums[mid] < target) {
                l = mid + 1;
            } else {
                r = mid;
            }
        }
        
        lowerBound = l;
        
        l = 0;
        r = nums.length;
        // l - first element that is > target
        while (l < r) {
            mid = (l + r) / 2;
            if (nums[mid] <= target) {
                l = mid + 1;
            } else {
                r = mid;
            }
        }
        upperBound = l - 1;
        
        if (lowerBound < nums.length && upperBound >= 0 && nums[upperBound] == target) { // 最后一个条件也可以是 nums[lowerBound] == target // 这里叫这个名字有点confusing，其实指的是如果target存在情况下的lower和upper.
            return new int[] {lowerBound, upperBound};
        } else {
            return new int[] {-1, -1};
        }
    }
}
```

