## Sqrt(x)

> Implement `int sqrt(int x)`.

### Solution

一个一个试。 Linear time.

```java
// Time Limit Exceeded
class Solution {
    public int mySqrt(int x) {
        int i = 1;
        while (i * i < x) {
            i += 1;
        }
        if (i * i == x) {
            return i;
        } else {
            return i - 1;
        }
    }
}
```

本质是不是一个搜索问题？那能不能用更快的搜索方法？

```java
// TLE
class Solution {
    public int mySqrt(int x) {
        int left = 0, right = x;
        while (left < right) {
            int mid = (left + right) / 2;
            long sq = mid * mid;
            if (sq < x) {
                left = mid + 1;
            } else if (sq > x) {
                right = mid;
            } else {
                return mid;
            }
        }
        if (right * right == x) {
            return right;
        } else {
            return right - 1;
        }
    }
}

// 除法更快？？？Accepted.
class Solution {
    public int mySqrt(int x) {
        if (x == 0) return 0;
        
        int left = 1, right = x; // start fron 1 to avoid divide by zero!
        while (left < right) {
            int mid = (left + right) / 2;
            if (mid < x / mid) {
                left = mid + 1;
            } else if (mid > x / mid) {
                right = mid;
            } else {
                return mid;
            }
        }
        if (right * right == x) {
            return right;
        } else {
            return right - 1;
        }
    }
}
```

更简单的Binary Search写法

```java
class Solution {
    public int mySqrt(int x) {
        int left = 0, right = x + 1;
        while (left < right) {
            int mid = (left + right) >> 1;
            long sq = mid * mid;
            if (sq == x) {
                return mid;
            } else if (sq < x) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        return left - 1;
    }
}
```

