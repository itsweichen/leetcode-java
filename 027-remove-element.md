## Remove Element

> Given an array nums and a value val, remove all instances of that value in-place and return the new length.

把逻辑想清楚再写代码。

* 明确每个指针的作用是什么。

```java
// 46.71%
class Solution {
    public int removeElement(int[] nums, int val) {
        //Error 1 - Wrong Answer - 按照代码执行，不要想当然
        int i = 0;
        int j = 0;
        int len = nums.length;
        
        while (j < len) {
            if (nums[i] == val) {
                while (j < len && nums[j] == val) {
                    j += 1;
                }
            }
            if (j < len) {
                int temp = nums[j];
                nums[j] = nums[i];
                nums[i] = temp;
                i += 1;
                j += 1;
            }
        }
        
        return i;
    }
}
```

看起来这题跟26题的套路一样呀