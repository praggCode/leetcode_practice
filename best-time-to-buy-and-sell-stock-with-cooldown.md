# Best Time to Buy and Sell Stock with Cooldown

## Problem

You are given an array prices where prices[i] is the price of a given stock on the ith day.

Find the maximum profit you can achieve. You may complete as many transactions as you like with the following restriction:

After you sell your stock, you cannot buy stock on the next day (cooldown one day).

You may not engage in multiple transactions simultaneously.

Example 1

Input: prices = [1,2,3,0,2]  
Output: 3  
Explanation: transactions = [buy, sell, cooldown, buy, sell]

Example 2

Input: prices = [1]  
Output: 0

Constraints

1 <= prices.length <= 5000  
0 <= prices[i] <= 1000

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
                skip = helper(idx + 1, True)
                memo[(idx, can_buy)] = max(buy, skip)
            else:
                sell = prices[idx] + helper(idx + 2, True)
                skip = helper(idx + 1, False)
                memo[(idx, can_buy)] = max(sell, skip)
                
            return memo[(idx, can_buy)]

        return helper(0, True)