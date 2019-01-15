## Longest Common Prefix

> Write a function to find the longest common prefix string amongst an array of strings.

### Solution

Draft

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        // Error - if length = 1: should not return ""!
        if (strs.length == 0) {
            return "";
        }
        
        int prefixLen = strs[0].length();
        
        if (prefixLen == 0) {
            return "";
        }
        
        for (int i = 1; i < strs.length; i++) {
            int j = 0;
            while (j < strs[i].length() && j < strs[0].length() && strs[i].charAt(j) == strs[0].charAt(j)) {
                j += 1;
            }
            // Error - Wrong Answer: j, not j + 1!
            prefixLen = j < prefixLen ? j : prefixLen;
        }
        
        return strs[0].substring(0, prefixLen);
    }
}
```

Final

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs.length == 0) {
            return "";
        }
        
        int prefixLen = strs[0].length();

        for (int i = 1; i < strs.length; i++) {
            int j = 0;
            while (j < strs[i].length() && j < strs[0].length() && strs[i].charAt(j) == strs[0].charAt(j)) {
                j += 1;
            }
            prefixLen = j < prefixLen ? j : prefixLen;
        }
        
        return strs[0].substring(0, prefixLen);
    }
}
```

