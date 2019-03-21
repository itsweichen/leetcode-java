## Combination Sum

> Given a **set** of candidate numbers (`candidates`) **(without duplicates)** and a target number (`target`), find all unique combinations in `candidates` where the candidate numbers sums to `target`.
>
> The **same** repeated number may be chosen from `candidates` unlimited number of times.
>
> **Note:**
>
> - All numbers (including `target`) will be positive integers.
> - The solution set must not contain duplicate combinations.

### Solution

Backtracking

* Note the `startIndex`

```java
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> res = new ArrayList<>();
        bt(res, candidates, target, new LinkedList<Integer>(), 0, 0);
        return res;
    }
    
    private void bt(List<List<Integer>> res, int[] candidates, int target, LinkedList<Integer> tmp, int curSum, int startIndex) {
        if (curSum < target) {
            for (int i = startIndex; i < candidates.length; i++) {
                tmp.add(candidates[i]);
                bt(res, candidates, target, tmp, curSum + candidates[i], i);
                tmp.removeLast(); // removeLast is from LinkedList, not from List interface!
            }
        } else if (curSum == target) {
            res.add(new ArrayList<>(tmp));
        }
    }
}
```

