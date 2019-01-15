## Majority Element

> Given an array of size *n*, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.
>
> You may assume that the array is non-empty and the majority element always exist in the array.

### Solution

**HashMap**

* Time: $O(n)$
* Space: $O(n)$

**Sort**

Use the middle element as the majority one.

* Time: $O(nlogn)$
* Space: $O(1)$

**Bit Manipulation**

For each bit, pick the one that appears the most.

* Time: $O(n)$
* Space: $O(1)$

**Fighting**

Image there are two tribes fighting for each other and one counteracts the other.

* Time: $O(n)$
* Space: $O(1)$



```java
// Bit manipulation - 46%
// 把 mask 每次移一位比这个要慢，为啥？
class Solution {
    public int majorityElement(int[] nums) {
        int len = nums.length;
        int majority = 0;
        for (int i = 0; i < 32; i++) {
            int mask = 1 << i;
            int count = 0;
            for (int j = 0; j < len; j++) {
                if ((nums[j] & mask) != 0) { // needs bracket!
                    count += 1;
                }
                if (count > len / 2) {
                    majority |= mask;
                    break;
                }
            }
        }
        return majority;
    }
}
```

