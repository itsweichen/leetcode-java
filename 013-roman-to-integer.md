## Roman to Integer

### Solution

别看这题简单，错了好多，做了好久。

1. 代码写复杂后容易出小错误。
2. if-else 逻辑很容易搞错。

**还能不能总结一下规律？**

```java
class Solution {
    public int romanToInt(String s) {
        Map<Character, Integer> symbolValueMap = new HashMap<>();
        symbolValueMap.put('I', 1);
        symbolValueMap.put('V', 5);
        symbolValueMap.put('X', 10);
        symbolValueMap.put('L', 50);
        symbolValueMap.put('C', 100);
        symbolValueMap.put('D', 500);
        symbolValueMap.put('M', 1000);
        
        int res = 0;
        int len = s.length();
        for (int i = 0; i < len; i++) {
            char cur = s.charAt(i);
            if (i + 1 < len) {
                char next = s.charAt(i + 1);
                boolean iTuple = cur == 'I' && (next == 'V' || next == 'X');
                boolean xTuple = cur == 'X' && (next == 'L' || next == 'C');
                boolean cTuple = cur == 'C' && (next == 'D' || next == 'M');
                if (iTuple || xTuple || cTuple) {
                    res += symbolValueMap.get(next) - symbolValueMap.get(cur);
                    i += 1;
                    continue;
                }
            }
            res += symbolValueMap.get(cur);
        }
        return res;
    }
}
```

如果前面小于后面的，就需要相减

Draft 1

* 注意Character和String的区别
* 

```java
class Solution {
    public int romanToInt(String s) {
        Map<Character, Integer> symbolValueMap = new HashMap<>();
        symbolValueMap.put('I', 1);
        symbolValueMap.put('V', 5);
        symbolValueMap.put('X', 10);
        symbolValueMap.put('L', 50);
        symbolValueMap.put('C', 100);
        symbolValueMap.put('D', 500);
        symbolValueMap.put('M', 1000);
        
        int res = 0;
        int len = s.length();
        for (int i = 0; i < len; i++) {
            if (s.charAt(i) == 'I' && i + 1 < len) {
                if (s.charAt(i+1) == 'V') {
                    res += 4;
                    i += 1;
                }
                else if (s.charAt(i+1) == 'X') {
                    res += 9;
                    i += 1;
                } else {
                    res = res + symbolValueMap.get(s.charAt(i));
                }
            } else if (s.charAt(i) == 'X' && i + 1 < len) {
                if (s.charAt(i+1) == 'L') {
                    res += 40;
                    i += 1;
                }
                else if (s.charAt(i+1) == 'C') {
                    res += 90;
                    i += 1;
                } else {
                    res = res + symbolValueMap.get(s.charAt(i));
                }
            } else if (s.charAt(i) == 'C' && i + 1 < len) {
                if (s.charAt(i+1) == 'D') {
                    res += 400;
                    i += 1;
                }
                else if (s.charAt(i+1) == 'M') {
                    res += 900;
                    i += 1;
                } else {
                    res = res + symbolValueMap.get(s.charAt(i));
                }
            } else {
                res = res + symbolValueMap.get(s.charAt(i));
            }
        }
        return res;
    }
}
```

