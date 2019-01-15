## Binary Tree Postorder Traversal

> Given a binary tree, return the *postorder* traversal of its nodes' values.

### Solution

Iteration. 虽然是Hard，但是也跟preorder的很像。关键是知道stack在整个过程中是怎么使用的，以及如何想办法在第二次访问一个node的时候再pop出来。

```java
class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        Stack<TreeNode> stack = new Stack<>();
        Set<TreeNode> rightVisitedSet = new HashSet<>();
        
        TreeNode node = root;
        
        while(node != null) {
            stack.push(node);
            node = node.left;
        }
        
        while (!stack.empty()) {
            node = stack.peek();
            if (rightVisitedSet.contains(node)) {
                stack.pop();
                res.add(node.val);
            } else {
                rightVisitedSet.add(node);
                node = node.right;
                while(node != null) {
                    stack.push(node);
                    node = node.left;
                }
            }
        }
        
        return res;
    }
}
```

Recursion.

```java
// 86%
class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        if (root == null) {
            return res;
        }
        postorder(root, res);
        return res;
    }
    
    private void postorder(TreeNode node, List<Integer>res) {
        if (node.left != null) {
            postorder(node.left, res);
        }
        if (node.right != null) {
            postorder(node.right, res);
        }
        res.add(node.val);
    }
}
```

