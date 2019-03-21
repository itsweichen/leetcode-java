## Valid Parentheses

> Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.
>
> An input string is valid if:
>
> 1. Open brackets must be closed by the same type of brackets.
> 2. Open brackets must be closed in the correct order.
>
> Note that an empty string is also considered valid.

### Solution

```java
class Solution {
    public boolean isValid(String s) {
        Map<Character, Character> rightLeftBracketMap = new HashMap<>();
        // Error - need to use '' instead of "" (String cannot be converted to Character)
        rightLeftBracketMap.put(')', '(');
        rightLeftBracketMap.put('}', '{');
        rightLeftBracketMap.put(']', '[');
        
        Stack stack = new Stack();
        for (int i = 0; i < s.length(); i++) {
            char cur = s.charAt(i);
            if (rightLeftBracketMap.containsKey(cur)) {
                // Can only use pop in if statement, but making the code harder to understand because the pop is inside if statement.
                if (!stack.empty() && stack.peek() == rightLeftBracketMap.get(cur)) {
                    stack.pop();
                } else {
                    return false;
                }
            } else {
                stack.push(cur);
            }
        }
        
        if (stack.empty()) {
            return true;
        } else {
            return false;
        }
    }
}
```

