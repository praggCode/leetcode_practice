# Coin Change II

## Problem

You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the number of combinations that make up that amount. If that amount cannot be made up by any combination of the coins, return 0.

You may assume that you have an infinite number of each kind of coin.

The answer is guaranteed to fit into a signed 32-bit integer.

Example 1

Input: amount = 5, coins = [1,2,5]  
Output: 4  

Explanation  
There are four ways to make up the amount:  
5 = 5  
5 = 2 + 2 + 1  
5 = 2 + 1 + 1 + 1  
5 = 1 + 1 + 1 + 1 + 1  

Example 2

Input: amount = 3, coins = [2]  
Output: 0

Example 3

Input: amount = 10, coins = [10]  
Output: 1

Constraints

1 <= coins.length <= 300  
1 <= coins[i] <= 5000  
All the values of coins are unique.  
0 <= amount <= 5000

## Solution

```python
class Solution(object):
    def change(self, amount, coins):
        memo = {}
        def helper(idx, total):
            if idx >= len(coins) or total > amount:
                return 0
            if total == amount:
                return 1
            if (idx, total) in memo:
                return memo[(idx, total)]
            take = helper(idx, total + coins[idx])
            not_t = helper(idx + 1, total)
            memo[(idx, total)] = take + not_t
            return memo[(idx, total)]
            
        return helper(0, 0)