## Balanced Binary Tree

> Given a binary tree, determine if it is height-balanced.
>
> **a binary tree in which the depth of the two subtrees of *every* node never differ by more than 1.**

### Solution

定义很重要！

这里并不需要定义专门一个object来存depth和是否是balanced，用 `-1` 就好啦。

```java
// 99.69%
class Solution {
    
    public boolean isBalanced(TreeNode root) {
        int d = depth(root);
        return d != -1;
    }
    
    private int depth(TreeNode node) {
        if (node == null) {
            return 0;
        }
        
        int left = this.depth(node.left);
        int right = this.depth(node.right);
        
        if (left == -1 || right == -1 || Math.abs(left - right) > 1) {
            return -1;
        }
        return Math.max(left, right) + 1;
    }
}
```

