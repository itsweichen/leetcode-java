## Symmetric Tree

>  Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

### Solution

1-PASS-AWARD!

这题的关键是要从subproblem的角度来想问题，虽然一开始不是很staightforward。

==再试试iteratively来做==

```java
// 30%
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public boolean isSymmetric(TreeNode root) {
        if (root == null) {
            return true;
        }
        return isSubtreeSymmetric(root.left, root.right);
    }
    
    private boolean isSubtreeSymmetric(TreeNode left, TreeNode right) {
        if (left != null && right != null) {
            if (left.val != right.val) {
                return false;
            }
            boolean outer = isSubtreeSymmetric(left.right, right.left);
            boolean inner = isSubtreeSymmetric(left.left, right.right);
            return outer && inner;
        } else if (left == null && right == null) {
            return true;
        } else {
            return false;
        }
    }
}
```

