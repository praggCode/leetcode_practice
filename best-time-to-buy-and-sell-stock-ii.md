# Best Time to Buy and Sell Stock II

## Problem

You are given an integer array prices where prices[i] is the price of a given stock on the ith day.

On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can sell and buy the stock multiple times on the same day, ensuring you never hold more than one share of the stock.

Find and return the maximum profit you can achieve.

Example 1

Input: prices = [7,1,5,3,6,4]  
Output: 7  
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 4.  
Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 3.  
Total profit = 7.

Example 2

Input: prices = [1,2,3,4,5]  
Output: 4

Example 3

Input: prices = [7,6,4,3,1]  
Output: 0

Constraints

1 <= prices.length <= 3 * 10^4  
0 <= prices[i] <= 10^4

## Solution

```python
class Solution(object):
    def maxProfit(self, prices):
        memo = {}
        def helper(idx, can_buy):
            if idx >= len(prices):
                return 0
            if (idx, can_buy) in memo:
                return memo[(idx, can_buy)]
            if can_buy:
                buy = -prices[idx] + helper(idx + 1, False)
                not_buy = helper(idx + 1, True)
                profit = max(buy, not_buy)
            else:
                sell = prices[idx] + helper(idx + 1, True)
                not_sell = helper(idx + 1, False)
                profit = max(sell, not_sell)

            memo[(idx, can_buy)] = profit
            return profit

        return helper(0, True)