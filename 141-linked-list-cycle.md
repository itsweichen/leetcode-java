## Linked List Cycle

> Given a linked list, determine if it has a cycle in it.

### Solution

Use a hashmap and see if the next pointer points to some node that has been seen before.

A tricky solution is to use two pointers, one faster than the other. What is the run time complexity for this?

```java
// 41%
public class Solution {
    public boolean hasCycle(ListNode head) {
        if (head == null) {
            return false;
        }
        
        ListNode slow = head;
        ListNode fast = head.next;
        
        while (fast != null) {
            if (fast == slow) {
                return true;
            }
            
            if (fast.next != null) {
                fast = fast.next.next;
            } else {
                return false;
            }
            slow = slow.next;
        }
        
        return false;
        
    }
}
```

