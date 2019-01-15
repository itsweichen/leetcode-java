## Factorial Trailing Zeros

> Given an integer *n*, return the number of trailing zeroes in *n*!.

### Solution

用数学的方法分析一下。

参见《编程之美》

```java
// 解法一：TLE
class Solution {
    public int trailingZeroes(int n) {
        int ret = 0;
        for (int i = 1; i <= n; i++) {
            int j = i;
            while (j % 5 == 0) {
                j = j / 5;
                ret++;
            }
        }
        return ret;
    }
}

// 解法二

```

