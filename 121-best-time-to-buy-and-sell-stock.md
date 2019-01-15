## Best Time to Buy and Sell Stock

> Say you have an array for which the *i* th element is the price of a given stock on day *i*.
>
> If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.
>
> Note that you cannot sell a stock before you buy one.

这题很有意思，想到了就很容易。关键点在于抓住，对于看过的数字，前面最小的数永远是最小的数，即当看到第 i 个数时，前面最小的数要么是之前 i - 1 那个最小的，要么是第 i 个。

### Solution

```java
class Solution {
    public int maxProfit(int[] prices) {
        int maxProfit = 0;
        int minPrice = Integer.MAX_VALUE;
        
        for (int i = 0; i < prices.length; i++) {
            minPrice = Math.min(minPrice, prices[i]);
            maxProfit = Math.max(prices[i] - minPrice, maxProfit);
        }
        
        return maxProfit;
    }
}
```





