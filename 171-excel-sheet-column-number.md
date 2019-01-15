## Excel Sheet Column Number

> Given a column title as appear in an Excel sheet, return its corresponding column number.



26进制问题。

```java
// 38%
class Solution {
    public int titleToNumber(String s) {
        int res = 0;
        int len = s.length();
        for (int i = len - 1; i >= 0; i--) {
            char c = s.charAt(i);
            res += charToNumber(c) * Math.pow(26, len - i - 1);
        }
        return res;
    }
    
    public int charToNumber(char c) {
        return c - 'A' + 1;
    }
}
```

