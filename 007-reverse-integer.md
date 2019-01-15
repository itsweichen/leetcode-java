## Reverse Integer

> Given a 32-bit signed integer, reverse digits of an integer.

### Solution

You don't need an extra array to store values, just pop and push in the same loop.

Note how to deal with overflow - shouldn't be too hard if you think about it.

```java
class Solution {
    public int reverse(int x) {
        // Integer.MAX_VALUE: 2^31 - 1 = 2,147,483,647
        // Integer.MIN_VALUE: -2^31 = -2,147,483,648
        int res = 0;
        while (x != 0) {
            int pop = x % 10;
            x = x / 10; // Note that -0 / 10 = 0;
            if (res > Integer.MAX_VALUE / 10 || res == Integer.MAX_VALUE / 10 && pop > 7 ) return 0;
            if (res < Integer.MIN_VALUE / 10 || res == Integer.MIN_VALUE / 10 && pop < -8) return 0;
            res = res * 10 + pop;
        }
        return res;
    }
}
```

**Follow Up**

如果是小数怎么办？