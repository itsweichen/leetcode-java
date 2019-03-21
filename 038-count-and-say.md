## Count and Say

> The count-and-say sequence is the sequence of integers with the first five terms as following:
>
> ```
> 1.     1
> 2.     11
> 3.     21
> 4.     1211
> 5.     111221
> ```
>
> `1` is read off as `"one 1"` or `11`.
> `11` is read off as `"two 1s"` or `21`.
> `21` is read off as `"one 2`, then `one 1"` or `1211`.
>
> Given an integer *n* where 1 ≤ *n* ≤ 30, generate the *n*th term of the count-and-say sequence.
>
> Note: Each term of the sequence of integers will be represented as a string.

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

