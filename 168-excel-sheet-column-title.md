## Excel Sheet Column Title

> Given a positive integer, return its corresponding column title as appear in an Excel sheet.



```java
// Where is the bug?

class Solution {
    public String convertToTitle(int n) {
        int num = n;
        StringBuilder strb = new StringBuilder();
        while (num != 0) {
            int rem = num % 26;
            strb.insert(0, intToChar(rem));
            num = num / 26;
        }
        return strb.toString();
    }
    
    private char intToChar(int n) {
        if (n == 0) {
            return 'Z';
        }
        return (char)('A' + n - 1); //不强制转换：possible lossy conversion from int to char
    }
}
```

还是没有想的很明白。

```java
class Solution {
    public String convertToTitle(int n) {
        int num = n;
        StringBuilder strb = new StringBuilder();
        while (num != 0) {
            int rem = num % 26;
            strb.insert(0, intToChar(rem));
            if (rem == 0) num -= 1; //!!!
            num = num / 26;
        }
        return strb.toString();
    }
    
    private char intToChar(int n) {
        if (n == 0) {
            return 'Z';
        }
        return (char)('A' + n - 1);
    }
}
```

更好的办法是这样 (from [here](https://leetcode.com/problems/excel-sheet-column-title/discuss/51399/Accepted-Java-solution))

```java
public class Solution {
    public String convertToTitle(int n) {
        StringBuilder result = new StringBuilder();

        while(n>0){
            n--;
            result.insert(0, (char)('A' + n % 26));
            n /= 26;
        }

        return result.toString();
    }
}
```

因为这里从 1 到 26，如果是 base-26 的话应该是 0 到 25，所以每次取个位的时候减去1.