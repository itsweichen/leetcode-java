## Binary Tree Preorder Traversal

> Given a binary tree, return the *preorder* traversal of its nodes' values.

### Solution

Recursive 很简单，==iterative 还需要再想想==。

迭代 思路二

* 这个思路要简单很多！
* 感觉是理解了stack的精髓之后想出来的，而不是仅仅在于模仿recursion的调用方式
  * 其实也不是，如果把recursion的调用方式想象成 “把下一步压栈”，而不是把 “当前元素压栈”，好像就说得通了？

```java
// 85%
class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
        Stack<TreeNode> stack = new Stack<>();
        List<Integer> res = new ArrayList<>();
        
        if (root == null) {
            return res;
        }
        
        stack.push(root);
        while(!stack.empty()) {
            TreeNode node = stack.pop();
            res.add(node.val);
            if (node.right != null) {
                stack.push(node.right);
            }
            if (node.left != null) {
                stack.push(node.left);
            }
        }
        
        return res;
    }
}
```

迭代 思路一

```java
// 85%
class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        if (root == null) {
            return res;
        }
        
        Stack<TreeNode> stack = new Stack<>();
        
        TreeNode node = root;
        while(node != null) {
            res.add(node.val);
            stack.push(node);
            node = node.left;
        }

        while(!stack.empty()) {
            node = stack.pop(); // 这里pop出来了，跟recursion实际的栈还不太一样 -- 其实也可以想成一样，因为函数返回就结束了
            node = node.right;
            while (node != null) {
                res.add(node.val);
                stack.push(node);
                node = node.left;
            }
        }
        
        return res;
    }
}
```

递归

```java
// 100%
class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> res = new LinkedList<>();
        if (root == null) return res;
        preorder(root, res);
        return res;
    }
    
    // node should not be null
    private void preorder(TreeNode node, List<Integer> res) {
        res.add(node.val);
        if (node.left != null) preorder(node.left, res);
        if (node.right != null) preorder(node.right, res);
    }
}
```

