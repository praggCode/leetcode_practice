# Best Time to Buy and Sell Stock III

## Problem

You are given an array prices where prices[i] is the price of a given stock on the ith day.

Find the maximum profit you can achieve. You may complete at most two transactions.

You may not engage in multiple transactions simultaneously. You must sell the stock before buying again.

Example 1

Input: prices = [3,3,5,0,0,3,1,4]  
Output: 6  
Explanation: Buy on day 4 (price = 0) and sell on day 6 (price = 3), profit = 3.  
Then buy on day 7 (price = 1) and sell on day 8 (price = 4), profit = 3.

Example 2

Input: prices = [1,2,3,4,5]  
Output: 4  
Explanation: Buy on day 1 and sell on day 5.

Example 3

Input: prices = [7,6,4,3,1]  
Output: 0

Constraints

1 <= prices.length <= 10^5  
0 <= prices[i] <= 10^5

## Solution

```python
class Solution(object):
    def maxProfit(self, prices):
        memo = {}

        def helper(pos, can_buy, transaction):
            if pos >= len(prices):
                return 0

            if (pos, can_buy, transaction) in memo:
                return memo[(pos, can_buy, transaction)]

            profit = 0

            if transaction < 2:
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
