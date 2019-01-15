## Reverse Word in a String

> Given an input string, reverse the string word by word.

### Solution

With Java API

* Split each word, and construct a new array.

Use pointers to traverse from the end, and find about each word and construct a new array

```java
public class Solution {
    public String reverseWords(String s) {
        
        List<String> strList = new ArrayList<>();
        int i = s.length() - 1;
        
        while (i >= 0) { // i > **or equal to** 0
            // skip spaces
            while (i >= 0 && s.charAt(i) == ' ') {
                i--;
            }
            
            int end = i;
            // find the word
            while (i >= 0 && s.charAt(i) != ' ') {
                i--;
            }
            
            String sub = s.substring(i + 1, end + 1);
            
            if (!sub.isEmpty()) { // substring will return empty if given the same index
                strList.add(sub);
            }
        }
        
        return String.join(" ", strList);
    }
}
```

