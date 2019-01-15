## Longest Palindromic Substring

> Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s** is 1000.

### Solution

**DP**

找到subproblem，然后知道填表的方式。

```java
// 5.46% 
class Solution {
    public String longestPalindrome(String s) {
        if (s.length() == 0) {
            return "";
        }
        
        int n = s.length();
        char[][] m = new char[n][n];
        
        int maxLen = 1;
        String maxStr = s.substring(0, 1);
        
        // 对角线填表
        for (int i = 0; i < n; i++) {
            m[i][i] = 'T';
        }
        
        for (int i = 0; i < n - 1; i++) {
            if (s.charAt(i) == s.charAt(i + 1)) {
                m[i][i + 1] = 'T';
                maxStr = s.substring(i, i + 2);
            } else {
                m[i][i + 1] = 'F';
            }
        }
        
        // 这里怎么写要想清楚
        for (int offset = 2; offset < n; offset++) {
            for (int i = 0; i < n - offset; i++) {
                if (s.charAt(i) == s.charAt(i + offset) && m[i + 1][i + offset - 1] == 'T') {
                    m[i][i + offset] = 'T';
                    maxStr = s.substring(i, i + offset + 1);
                } else {
                    m[i][i + offset] = 'F';
                }
            }
        }
        
        return maxStr;
    }
}
```

