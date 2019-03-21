## Add Two Numbers

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order** and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

### Solution

注意：

* 哪怕再简单的题，也要带入例子跑一遍，像 `node = node.next` 或者 `i++` 这样的很容易忘掉。
* Java is pass (the reference) by value!!! 在定义子函数的时候千万小心！

```java
// 26%
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode node = dummy;
        int carry = 0;
        
        while(l1 != null && l2 != null) {
            int sum = l1.val + l2.val + carry;
            node.next = new ListNode(sum % 10);
            carry = sum / 10;
            node = node.next;
            l1 = l1.next; // !!!
            l2 = l2.next; // !!!
        }
        
        //carry = iterateRemaining(l1, node, carry);
        //carry = iterateRemaining(l2, node, carry);
        while (l1 != null) {
            int sum = l1.val + carry;
            node.next = new ListNode(sum % 10);
            carry = sum / 10;
            node = node.next;
            l1 = l1.next;
        }
        
        while (l2 != null) {
            int sum = l2.val + carry;
            node.next = new ListNode(sum % 10);
            carry = sum / 10;
            node = node.next;
            l2 = l2.next;
        }
        
        if (carry > 0) {
            node.next = new ListNode(carry);
        }
        
        return dummy.next;
    }
}
```

用 `||` 能写得更简洁。

```java
// 16%
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode node = dummy;
        int carry = 0;
        
        while(l1 != null || l2 != null) {
            int x = (l1 != null) ? l1.val : 0;
            int y = (l2 != null) ? l2.val : 0;
            int sum = x + y + carry;
            node.next = new ListNode(sum % 10);
            carry = sum / 10;
            node = node.next;
            if (l1 != null) l1 = l1.next;
            if (l2 != null) l2 = l2.next;
        }

        if (carry > 0) {
            node.next = new ListNode(carry);
        }
        
        return dummy.next;
    }
}
```

