## Container With Most Water

> Given *n* non-negative integers *a1*, *a2*, ..., *an* , where each represents a point at coordinate (*i*, *ai*). *n* vertical lines are drawn such that the two endpoints of line *i* is at (*i*, *ai*) and (*i*, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.
>
> **Note:** You may not slant the container and *n* is at least 2.

### Solution

**Brute Force** 的方法显而易见，把每对pair试一遍就好。

想想有没有可以 O(n) 解决的方法。如果我们用两根指针的话，面积的计算公式为

$area = (j - i) * min(a[i], a[j])$

这里有两个关键问题

1. 指针的初始位置放哪？
2. 怎么移动指针？

第一个问题有几种方案，头、尾、中间、一头一尾。如果先把两个指针放在一头一尾，随着他们往中间会移动，乘号前面的会变小，所以我们希望后部分变大。又后部分受限于更矮的柱子。如果我们移动两个之中高的，那么移动的结果肯定会导致面积变小，所以我们只有移动矮柱子，才能使最后的面积有可能变大。这其实就是一种 **Greedy** 的方法。

```java
class Solution {
    public int maxArea(int[] height) {
        int i = 0, j = height.length - 1;
        int maxArea = Integer.MIN_VALUE;
        while (i < j) {
            int curArea = (j - i) * Math.min(height[i], height[j]);
            maxArea = curArea > maxArea ? curArea : maxArea;
            if (height[i] <= height[j]) {
                i++;
            } else {
                j--;
            }
        }
        return maxArea;
    }
}
```



