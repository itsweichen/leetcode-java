## Group Anagrams

> Given an array of strings, group anagrams together.

### Solution

合理设计数据结构。

Complexity - n = m * k 是字母总数，m 是单词书，单词平均长度是 k

* Time: $O(mklog(k))​$ - 排序
* Space: $O(n) = O(mk)$

喵老师说可以使用桶排序。

```java
// 75%
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();
        
        for (String str: strs) {
            String sortedStr = sortString(str);
            if (map.containsKey(sortedStr)) {
                List<String> list = map.get(sortedStr);
                list.add(str);
            } else {
                List<String> list = new ArrayList<>();
                list.add(str);
                map.put(sortedStr, list);
            }
        }
        
        // return map.values().stream().collect(Collectors.toCollection(ArrayList::new));
        return new ArrayList(map.values());
    }
    
    private String sortString(String str) {
        char[] charArray = str.toCharArray();
        Arrays.sort(charArray);
        return new String(charArray);
    }
}
```