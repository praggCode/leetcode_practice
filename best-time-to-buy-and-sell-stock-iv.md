# Best Time to Buy and Sell Stock IV

## Problem

You are given an integer array prices where prices[i] is the price of a given stock on the ith day, and an integer k.

Find the maximum profit you can achieve. You may complete at most k transactions.

You may not engage in multiple transactions simultaneously. You must sell the stock before buying again.

Example 1

Input: k = 2, prices = [2,4,1]  
Output: 2  
Explanation: Buy on day 1 and sell on day 2.

Example 2

Input: k = 2, prices = [3,2,6,5,0,3]  
Output: 7  
Explanation: Buy on day 2 and sell on day 3, then buy on day 5 and sell on day 6.

Constraints

1 <= k <= 100  
1 <= prices.length <= 1000  
0 <= prices[i] <= 1000

## Solution

```python
class Solution(object):
    def maxProfit(self, k, prices):
        memo = {}

        def helper(pos, can_buy, transaction):
            if pos >= len(prices):
                return 0

            if (pos, can_buy, transaction) in memo:
                return memo[(pos, can_buy, transaction)]

            profit = 0

            if transaction < k:
                if can_buy:
                    buy = -prices[pos] + helper(pos + 1, False, transaction)
                    not_buy = helper(pos + 1, True, transaction)
                    profit = max(buy, not_buy)
                else:
                    sell = prices[pos] + helper(pos + 1, True, transaction + 1)
                    not_sell = helper(pos + 1, False, transaction)
                    profit = max(sell, not_sell)

                memo[(pos, can_buy, transaction)] = profit

            return profit

        return helper(0, True, 0)