## Remove Duplicates from Sorted List

> Given a sorted linked list, delete all duplicates such that each element appear only *once*.



```java
// 56%
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        
        while (fast != null) { // Not fast.next! 千万不要蜜汁自信！
            while (fast != null && slow.val == fast.val) {
                fast = fast.next;
            }
            slow.next = fast;
            slow = fast;
        }
        
        return head;
    }
}
```

