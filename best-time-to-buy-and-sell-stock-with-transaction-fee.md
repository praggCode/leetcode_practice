# Best Time to Buy and Sell Stock with Transaction Fee

## Problem

You are given an array prices where prices[i] is the price of a given stock on the ith day, and an integer fee representing a transaction fee.

Find the maximum profit you can achieve. You may complete as many transactions as you like, but you must pay the transaction fee for each transaction.

You may not engage in multiple transactions simultaneously.

Example 1

Input: prices = [1,3,2,8,4,9], fee = 2  
Output: 8  

Explanation  
Buy at price 1 and sell at 8.  
Buy at price 4 and sell at 9.

Example 2

Input: prices = [1,3,7,5,10,3], fee = 3  
Output: 6

Constraints

1 <= prices.length <= 5 * 10^4  
1 <= prices[i] < 5 * 10^4  
0 <= fee < 5 * 10^4

## Solution

```python
class Solution(object):
    def maxProfit(self, prices, fee):
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
                sell = prices[idx] - fee + helper(idx + 1, True)
                skip = helper(idx + 1, False)
                memo[(idx, can_buy)] = max(sell, skip)

            return memo[(idx, can_buy)]
            
        return helper(0, True)