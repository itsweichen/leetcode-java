## Implement strStr()

> Implement strStr().
>
> Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

### Solution



```java
// 44.26%
class Solution {
    public int strStr(String haystack, String needle) {
        int i = 0;
        
        // empty character literal: needle == ''
        if (needle.equals("")) {
            return 0;
        }
        
        while (i < haystack.length() - needle.length() + 1) {
            if (haystack.charAt(i) == needle.charAt(0)) {
                int j = 0;
                while (i + j < haystack.length() && j < needle.length() && haystack.charAt(i+j) == needle.charAt(j)) {
                    j += 1;
                }
                // Error - not j + 1!
                if (j == needle.length()) {
                    return i;
                }
            }
            i += 1;
        }
        
        return -1;
    }
}
```

