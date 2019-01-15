## Path Sum

> Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

同样的错误！没弄清 leaf 的概念！

**A leaf is a node with no children.**

```java
// WRONG ANSWER!
class Solution {
    public boolean hasPathSum(TreeNode root, int sum) {
        if (root == null) {
            return false;
        }
        
        return helper(root, sum);
    }
    
    private boolean helper(TreeNode root, int sum) {
        if (root == null) {
            if (sum == 0) {
                return true;
            } else {
                return false;
            }
        }
        
        return helper(root.left, sum - root.val) || helper(root.right, sum - root.val);
    }
}
```

