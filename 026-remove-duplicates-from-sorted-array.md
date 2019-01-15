## Remove Duplicates from Sorted Array

> Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.
>
> Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

### Solution

1-PASS-AWARD!

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 0) {
            return 0;
        }
        
        int i = 0;
        int j = 0;
        int len = nums.length;
        while (j < len) {
            while (j < len && nums[j] == nums[i]) {
                j += 1;
            }
            if (j < len) {
                i += 1;
                nums[i] = nums[j];
            }
        }
        return i + 1;
    }
}
```

