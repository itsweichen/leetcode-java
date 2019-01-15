## Permutations

> Given a collection of **distinct** integers, return all possible permutations.

### Solution

Backtracking

```java
// 114 ms
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> numsList = Arrays.stream(nums).boxed().collect(Collectors.toList());
        backtrack(new ArrayList(), numsList, res);
        return res;
    }
    
    private void backtrack(List<Integer> cur, List<Integer> remaining, List<List<Integer>> res) {
        if (remaining.size() == 0) {
            res.add(cur);
            return;
        }
        
        for (int i = 0; i < remaining.size(); i++) {
            List<Integer> curNew = new ArrayList<>(cur);
            curNew.add(remaining.get(i));
            List<Integer> remainingNew = new ArrayList<>(remaining);
            remainingNew.remove(i);
            
            backtrack(curNew, remainingNew, res);
        }
    }
}
```

感觉这才是真正的backtracking，上面的写法要建好多对象。[link](https://leetcode.com/problems/permutations/discuss/18239/A-general-approach-to-backtracking-questions-in-Java-(Subsets-Permutations-Combination-Sum-Palindrome-Partioning))

```java
public List<List<Integer>> permute(int[] nums) {
   List<List<Integer>> list = new ArrayList<>();
   backtrack(list, new ArrayList<>(), nums);
   return list;
}

private void backtrack(List<List<Integer>> list, List<Integer> tempList, int [] nums){
   if(tempList.size() == nums.length){
      list.add(new ArrayList<>(tempList));
   } else{
      for(int i = 0; i < nums.length; i++){ 
         if(tempList.contains(nums[i])) continue; // element already exists, skip
         tempList.add(nums[i]);
         backtrack(list, tempList, nums);
         tempList.remove(tempList.size() - 1);
      }
   }
} 
```

