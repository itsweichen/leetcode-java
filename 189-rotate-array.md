## Rotate Array

> Given an array, rotate the array to the right by *k* steps, where *k* is non-negative.

Use an extra array.

``` java
// 57%
class Solution {
    public void rotate(int[] nums, int k) {
        int len = nums.length;
        int[] temp = new int[len];
        
        for (int i = 0; i < len; i++) {
            temp[(i + k) % len] = nums[i];
        }
        for (int i = 0; i < len; i++) {
            nums[i] = temp[i];
        }
    }
}
```



每次移一位，循环K次 —— TLE.

* Time: $O(nk)$ - 注意不是$O(n)$
* Space: $O(1)$

```java
class Solution {
    public void rotate(int[] nums, int k) {
        k = k % nums.length;
        for (int i = 0; i < k; i++) {
            rotateByOne(nums);
        }
    }
    
    private void rotateByOne(int[] nums) {
        if (nums.length == 0) {
            return;
        }
        
        int last = nums[nums.length - 1];
        for (int i = nums.length - 1; i > 0; i--) {
            nums[i] = nums[i - 1];
        }
        
        nums[0] = last;
    }
}
```

