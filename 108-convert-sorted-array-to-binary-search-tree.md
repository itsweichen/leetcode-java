## Convert Sorted Array to Binary Search Tree

> Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

感觉这题是 算法基础题？

### Solution

关键是弄清楚什么是 height balanced BST。以及还是那句话，如何拆解subproblem.



```java
// 100%
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
    public TreeNode sortedArrayToBST(int[] nums) {
        TreeNode head = helper(nums, 0, nums.length - 1);
        return head;
    }
    
    private TreeNode helper(int[] nums, int start, int end) {
        if (start > end) {
            return null;
        }
        
        int mid = (start + end) / 2;
        TreeNode node = new TreeNode(nums[mid]);
        node.left = helper(nums, start, mid - 1);
        node.right = helper(nums, mid + 1, end);
        return node;
    }
}
```



