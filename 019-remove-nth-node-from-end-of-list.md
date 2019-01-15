##  Remove Nth Node From End of List

> Given a linked list, remove the *n*-th node from the end of list and return its head.

### Solution

**Intuitive**

* Do a two-pass of the list.

```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        
        // count the length
        int length = 0;
        ListNode node = dummy;
        while (node != null) {
            length++;
            node = node.next; 
        }
        
        // find the previous node
        node = dummy;
        int i = 1;
        while (i != length - n) {
            node = node.next;
            i++;
        }
        
        // remove
        if (node.next != null) {
            node.next = node.next.next;
        }
        
        return dummy.next;
    }
}
```

**Recursion**

只能想到Recursion了，但既然有stack，感觉还是两次啊（

```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        this.helper(dummy, n);
        return dummy.next;
    }
    
    public int helper(ListNode node, int n) {
        if (node == null) {
            return 0;
        }
        
        int next = helper(node.next, n);
        
        if (next == n && node.next != null) {
            node.next = node.next.next;
        }
        
        return next + 1;
    }
}
```

**Two Pointers !**

这个解法又十分奇妙了。

