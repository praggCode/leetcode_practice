# Climbing Stairs

## Problem

You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

Example 1

Input: n = 2  
Output: 2  
Explanation:  
1. 1 step + 1 step  
2. 2 steps

Example 2

Input: n = 3  
Output: 3  
Explanation:  
1. 1 step + 1 step + 1 step  
2. 1 step + 2 steps  
3. 2 steps + 1 step

Constraints

1 <= n <= 45

## Solution

```python
class Solution(object):
    def climbStairs(self, n):
        memo = {}

        def helper(n):
            if n < 3:
                return n

            if n in memo:
                return memo[n]

            memo[n] = helper(n - 2) + helper(n - 1)
            return memo[n]

        return helper(n)