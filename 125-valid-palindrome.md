## Valid Palindrome

> Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

Hint: two pointers.

发现好智障。。

```java
// 73%
class Solution {
    public boolean isPalindrome(String s) {
        
        int i = 0;
        int j = s.length() - 1  ;
        
        while (i < j) {
            char iChar = Character.toLowerCase(s.charAt(i));
            char jChar = Character.toLowerCase(s.charAt(j));
            if (notAlphanumeric(iChar) || notAlphanumeric(jChar)) {
                if (notAlphanumeric(iChar)) i += 1;
                if (notAlphanumeric(jChar)) j -= 1;
            } else {
                if (iChar == jChar) {
                    i += 1;
                    j -= 1;
                } else {
                    return false;
                }
            }
        }
        
        return true;
    }
    
    private boolean notAlphanumeric(char a) {
        return !Character.isLetterOrDigit(a);
    }
}
```

