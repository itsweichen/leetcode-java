## Palindrome Number

> Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

### Solution

**Convert to String**

Use two pointers and move them step by step together to the middle until they meet.

- Time:  $O(n)$
- Space:  $O(n)$

```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0) {
            return false;
        }
        
        String str = Integer.toString(x);
        
        int i = 0;
        int j = str.length() - 1;
        
        while (i < j) {
            if (str.charAt(i) != str.charAt(j)) {
                return false;
            }
            i += 1;
            j -= 1;
        }
        
        return true;
    }
}
```

**Reverse Integer**

Use the code from 007 to reverse the integer first.

- Time:  $O(n)$
- Space:  $O(1)$

> **Do you need to reverse the whole integer?**

**Reverse half of the number**

Notes

* How to determine when to reach half of the number?
* `1221` is easy. How to deal with `121`?

**TBD**

