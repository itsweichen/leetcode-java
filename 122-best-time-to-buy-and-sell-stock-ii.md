## Best Time to Buy and Sell Stock II

> Say you have an array for which the *i*th element is the price of a given stock on day *i*.
>
> Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).
>
> **Note:** You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).



这题画个图清楚很多，有点像找规律题。

注意这个case，最后几个数是一样大的，也要记得加上去。

 `[1,9,6,9,1,7,1,1,5,9,9,9]`



```java
class Solution {
    public int maxProfit(int[] prices) {
        if (prices.length < 2) {
            return 0;
        }
        
        int maxProfit = 0;
        int low = prices[0];
        for (int i = 1; i < prices.length; i++) {
            if (prices[i] <= prices[i - 1]) { // should be <= !
                maxProfit += prices[i - 1] - low;
                low = prices[i];
            }
        }
        if (prices[prices.length - 1] > prices[prices.length - 2]) {
            maxProfit += prices[prices.length - 1] - low;
        }
        return maxProfit;
    }
}

// 官方解法感觉要容易理解一些？
class Solution {
    public int maxProfit(int[] prices) {
        int i = 0;
        int valley = prices[0];
        int peak = prices[0];
        int maxprofit = 0;
        while (i < prices.length - 1) {
            while (i < prices.length - 1 && prices[i] >= prices[i + 1])
                i++;
            valley = prices[i];
            while (i < prices.length - 1 && prices[i] <= prices[i + 1])
                i++;
            peak = prices[i];
            maxprofit += peak - valley;
        }
        return maxprofit;
    }
}
```

然而最简单的是无脑做法

```java
class Solution {
    public int maxProfit(int[] prices) {
        int maxprofit = 0;
        for (int i = 1; i < prices.length; i++) {
            if (prices[i] > prices[i - 1])
                maxprofit += prices[i] - prices[i - 1];
        }
        return maxprofit;
    }
}
```

