## Intersection of Two Linked Lists

> Write a program to find the node at which the intersection of two singly linked lists begins.

### Solution

**HashMap**

* Time: $O(m + n)$
* Space: $O(m)$ or $(n)$

忘了Brute Force也是一种解法，只用 constant space 不过要用 $O(mn)$ time.

Hint：如何使用 two pointers 来实现 constant space 解法？

```java
// 54% - two pointers.
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null) { // 注意这里！
            return null;
        }
        
        ListNode p = headA;
        ListNode q = headB;
        
        while (p != null && q != null) {
            p = p.next;
            q = q.next;
        }
        
        if (p == null) p = headB;
        else q = headA;
        
        while (p != null && q != null) {
            p = p.next;
            q = q.next;
        }
        
        if (p == null) p = headB;
        else q = headA;
        
        while (p != null && q != null) {
            if (p == q) return p; // 最后一次check就好了！
            p = p.next;
            q = q.next;
        }
        
        return null;
    }
}
```

