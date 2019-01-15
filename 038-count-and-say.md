## Count and Say



### Solution

ONE-PASS-AWARD!!!

```java
// 59.93%
class Solution {
    public String countAndSay(int n) {
        if (n == 1) {
            return "1";
        }
        
        String input = "1";
        for (int i = 1; i < n; i++) {
            int p = 0;
            int q = 0;
            StringBuilder output = new StringBuilder();
            while (q < input.length()) {
                while (q < input.length() && input.charAt(p) == input.charAt(q)) {
                    q += 1;
                }
                output.append(q - p);
                output.append(input.charAt(p));
                p = q;
            }
            input = output.toString();
        }
        
        return input;
    }
}
```

