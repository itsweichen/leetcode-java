## Minimum Depth of Binary Tree

> Given a binary tree, find its minimum depth.
>
> The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

```java
// WRONG ANSWER!
class Solution {
    public int minDepth(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<>();
        
        int depth = 0;
        queue.add(root);
        while(!queue.isEmpty()) {
            int queueLen = queue.size();
            for (int i = 0; i < queueLen; i++) {
                TreeNode node = queue.poll();
                if (node == null) {
                    return depth;
                } else {
                    queue.add(node.left);
                    queue.add(node.right);
                }
            }
            depth += 1;
        }
        
        return depth;
    }
}
```

### Solution

BFS / Level-order traversal.

* Time: $O(n)$. In the worst case it would need to visit n/2 nodes for a balanced tree. It is slightly better than DFS becasue DFS needs to visit all nodes.
* Space: $O(n)$

```java
// 40%
class Solution {
    public int minDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        
        Queue<TreeNode> queue = new LinkedList<>();
        
        queue.add(root);
        int depth = 0;
        while(!queue.isEmpty()) {
            depth += 1;
            int queueSize = queue.size();
            for (int i = 0; i < queueSize; i++) {
                TreeNode node = queue.poll();
                if (node.left == null && node.right == null) {
                    return depth;
                }
                if (node.left != null) queue.add(node.left);
                if (node.right != null) queue.add(node.right);
            }
        }
        return depth;
    }
}
```

