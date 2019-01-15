## Climbing Stairs



Recursion含有冗余计算，可以用DP.

ONE-PASS.

```java
// 30%
class Solution {
    public int climbStairs(int n) {
        if (n == 1) {
            return 1;
        }
        
        int prev = 1;
        int cur = 1;
        
        for (int i = 2; i <= n; i++) {
            int temp = cur; // !!!
            cur = cur + prev;
            prev = temp;
        }
        
        return cur;
    }
}
```

