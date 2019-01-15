## Add Binary

> Given two binary strings, return their sum (also a binary string).

```java
// 16.66%
class Solution {
    public String addBinary(String a, String b) {
        // Add one by one
        
        int i = a.length() - 1;
        int j = b.length() - 1;
        
        int carry = 0;
        StringBuilder res = new StringBuilder();
        while (i >= 0 && j >= 0) {
            int iValue = Character.getNumericValue(a.charAt(i));
            int jValue = Character.getNumericValue(b.charAt(j));
            int value = iValue + jValue + carry;
            res.insert(0, value % 2);
            carry = value / 2;
            i -= 1;
            j -= 1;
        }
        
        while (i >= 0) {
            int value = Character.getNumericValue(a.charAt(i));
            value += carry;
            res.insert(0, value % 2);
            carry = value / 2;
            i -= 1;
        }
        
        while (j >= 0) {
            int value = Character.getNumericValue(b.charAt(j));
            value += carry;
            res.insert(0, value % 2);
            carry = value / 2;
            j -= 1;
        }
        
        if (carry > 0) {
            res.insert(0, 1);
        }
        
        return res.toString();
    }
}
```

