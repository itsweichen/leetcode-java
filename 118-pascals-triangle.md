## Pascal's Triangle

> Given a non-negative integer *numRows*, generate the first *numRows* of Pascal's triangle.

```java
// 62%
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> res = new ArrayList<>();
        
        if (numRows == 0) return res;
        
        res.add(new ArrayList<>());
        res.get(0).add(1);
        
        if (numRows == 1) return res;
        
        res.add(new ArrayList<>());
        res.get(1).add(1);
        res.get(1).add(1);
        
        if (numRows == 2) return res;
        
        for (int i = 3; i <= numRows; i++) {
            List<Integer> prev = res.get(i - 2);
            List<Integer> row = new ArrayList<>();
            res.add(row);
            for (int j = 0; j < i; j++) {
                if (j == 0 || j == i - 1) {
                    row.add(1);
                } else {
                    row.add(prev.get(j) + prev.get(j - 1)); // not i!
                }
            }
        }
        
        return res;
    }
}
```

