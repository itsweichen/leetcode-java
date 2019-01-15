## Plus One

> Given a non-empty array of digits representing a non-negative integer, plus one to the integer.

### Solution

```java
// 100%
class Solution {
    public int[] plusOne(int[] digits) {
        if (digits.length == 0) {
            return new int[] {1};
        }
        
        // 写之前注意最后一位要单独处理，因为跟别的不一样，不能放在循环里
        int len = digits.length;
        int value = digits[len - 1]  + 1;
        digits[len - 1] = value % 10;
        int carry = value / 10;
        
        if (carry > 0) {
            for (int i = len - 2; i > -1; i--) {
                value = digits[i] + carry;
                digits[i] = value % 10;
                carry = value / 10;
            }
        }
                
        if (carry > 0) {
            int[] res = new int[len + 1];
            res[0] = 1;
            for (int i = 0; i < len; i++) {
                res[i + 1] = digits[i];
            }
            return res;
        } else {
            return digits;
        }
    }
}
```

