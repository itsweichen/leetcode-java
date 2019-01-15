## Length of Last Word

> Given a string s consists of upper/lower-case alphabets and empty space characters `' '`, return the length of last word in the string.

什么奇怪的题...

需要更简洁的写法？

```java
// 100.00%
class Solution {
    public int lengthOfLastWord(String s) {
        if (s.length() == 0) {
            return 0;
        }
        
        int i = s.length() - 1;
        
        // Get rid of trailing spaces
        if (s.charAt(i) == ' ') {
            while (i >= 0 && s.charAt(i) == ' ') {
                i -= 1;
            }
            if (i == -1) {
                return 0;
            }
        }
        
        // Find the length
        int end = i;
        while (i >= 0 && s.charAt(i) != ' ') {
            i -= 1;
        }
        
        return end - i;
    }
}
```

