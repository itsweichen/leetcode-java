## Binary Search

假设数组前半段符合A要求，后半段不符合A。以下套路的结果

* left是不符合A的第一个数
* 如果想找符合A要求的最后一个数，返回 left - 1

```python
left = 0, right = len(nums)
while(left < right) {
    mid = (left + right) >> 1;
    if (A(nums[mid])) left = mid + 1;
    else right = mid;
}
```

**分析**

为什么 `mid` 不会 out of range?

* 如果 `len == 0`，那么不会进入循环
* 如果进入循环，意味着 `left < right`，`max(right)` 是 `len`，所以*在循环里* `max(left)` 是 `len - 1`
  * 这样的话 `mid = (left + right) / 2 <= (len + len - 1) / 2 < len`
  * 而且 `mid >= 0` 肯定是成立的

最后得到的 `left` 的范围是什么？

* 因为 `max(mid)` 是 `len - 1`，所以最后得到的 `max(left)` 是 `len`，即 `0 <= left <= len`
* 也就是说当整个数组都符合 A 要求时，`left = len` 就 out of range
  * 那么当整个数组都不符合 A 要求时，`left = 0`，这时候 `left - 1` 就 out of range 了因为等于 -1.

等等，既然 `mid >= 0` 而 `left = mid + 1`，`left` 怎么会等于0？

* 因为这种情况下 `left = mid + 1` 从来就没被执行过呀



