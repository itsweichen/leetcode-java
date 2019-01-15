## Merge Sorted Array

> Given two sorted integer arrays *nums1* and *nums2*, merge *nums2* into *nums1* as one sorted array.
>
> Example:
>
> ```
> Input:
> nums1 = [1,2,3,0,0,0], m = 3
> nums2 = [2,5,6],       n = 3
> 
> Output: [1,2,2,3,5,6]
> ```

### Solution

Typo, otherwise good!

```java
// 16%
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int p = m - 1;
        int q = n - 1;
        for (int i = m + n - 1; i >= 0; i--) {
            if (p >= 0 && q >= 0) {
                if (nums1[p] > nums2[q]) {
                    nums1[i] = nums1[p];
                    p -= 1;
                } else {
                    nums1[i] = nums2[q];
                    q -= 1;
                }
            } else if (q >= 0) {
                nums1[i] = nums2[q];
                q -= 1;
            } else {
                // i = p + q + 1
                // if q = -1, i = p, just return
                return;
            }
        }
    }
}
```

