## Binary Tree Inorder Traversal

> Given a binary tree, return the *inorder* traversal of its nodes' values.

### Solution

Recursion很直白，iteration的方法跟preorder很像，就是visit的时间点不一样。

Interation

```java
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        Stack<TreeNode> stack = new Stack<>();
        
        TreeNode node = root;
        while (node != null) {
            stack.push(node);
            node = node.left;
        }
        
        while(!stack.empty()) {
            node = stack.pop();
            res.add(node.val);
            node = node.right;
            while (node != null) {
                stack.push(node);
                node = node.left;
            }
        }
        
        return res;
    }
}
```

Recursion

```java
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        if (root == null) {
            return res;
        }
        inorder(root, res);
        return res;
    }
    
    private void inorder(TreeNode node, List<Integer> res) {
        if (node.left != null) {
            inorder(node.left, res);
        }
        res.add(node.val);
        if (node.right != null) {
            inorder(node.right, res);
        }
    }
}
```

