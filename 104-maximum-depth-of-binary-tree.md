## Maximum Depth of Binary Tree

> Given a binary tree, find its maximum depth.

```java
// BFS - 7%
class Solution {
    public int maxDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        
        Queue<TreeNode> q = new LinkedList<>();
        int level = 0;
        q.add(root);
        while (!q.isEmpty()) {
            level += 1;
            int queueLen = q.size(); // It's a collection, so not .length()
            for (int i = 0; i < queueLen; i++) {
                TreeNode node = q.poll();
                addIfNotNull(q, node.left);
                addIfNotNull(q, node.right);
            }
        }
        
        return level;
    }
    
    private void addIfNotNull(Queue q, TreeNode node) {
        if (node != null) {
            q.add(node);
        }
    }
}
```



```java

// DFS recursion - 100%
class Solution {
    public int maxDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        
        return Math.max(maxDepth(root.left) + 1, maxDepth(root.right) + 1);
    }
}
```

