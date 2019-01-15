## Longest Substring Without Repeating Characters

> Given a string, find the length of the **longest substring** without repeating characters.



### Solution

Two pointers by using a hash set.

```java
// 34%
class Solution {
    public int lengthOfLongestSubstring(String s) {
        Set<Character> set = new HashSet<>();
        
        int i = 0, j = 0;
        int maxLen = 0;
        while (j < s.length()) {
            char cur = s.charAt(j);
            if (!set.contains(cur)) {
                set.add(cur);
                maxLen = j - i + 1 > maxLen? j - i + 1 : maxLen;
                j += 1;
            } else {
                while(s.charAt(i) != cur) {
                    set.remove(s.charAt(i));
                    i += 1;
                }
                set.remove(s.charAt(i));
                i += 1;
            }
        }
        
        return maxLen;
    }
}
```

