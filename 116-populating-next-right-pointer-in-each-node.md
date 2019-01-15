##  Populating Next Right Pointers in Each Node

> Given a binary tree
>
> ```
> struct TreeLinkNode {
>   TreeLinkNode *left;
>   TreeLinkNode *right;
>   TreeLinkNode *next;
> }
> ```
>
> Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to `NULL`.
>
> Initially, all next pointers are set to `NULL`.

### Solution

Level-order traversal. This takes `O(n)` space though.

```java
// 30.10%
public class Solution {
    public void connect(TreeLinkNode root) {
        if (root == null) return;
        
        Queue<TreeLinkNode> queue = new LinkedList<>();
        queue.add(root);
        while(!queue.isEmpty()) {
            int queueSize = queue.size();
            for (int i = 0; i < queueSize; i++) {
                TreeLinkNode curNode = queue.poll();
                if (curNode.left != null) queue.add(curNode.left);
                if (curNode.right != null) queue.add(curNode.right);
                if (i != queueSize - 1) {
                    curNode.next = queue.peek();
                }
            }
        }
    }
}
```

