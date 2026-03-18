# Min Cost Climbing Stairs

## Problem

You are given an integer array cost where cost[i] is the cost of the ith step on a staircase. Once you pay the cost, you can climb either one or two steps.

You can start either from step 0 or step 1.

Return the minimum cost to reach the top of the floor.

Example 1

Input: cost = [10,15,20]  
Output: 15  

Explanation  
Start at index 1, pay 15, and climb two steps to reach the top.

Example 2

Input: cost = [1,100,1,1,1,100,1,1,100,1]  
Output: 6  

Explanation  
The minimum cost path accumulates to 6.

Constraints

2 <= cost.length <= 1000  
0 <= cost[i] <= 999

## Solution

```python
class Solution(object):
    def minCostClimbingStairs(self, cost):
        n = len(cost)
        if n == 1:
            return cost[0]
        first = cost[0]
        second = cost[1]
        for i in range(2, n):
            current = cost[i] + min(first, second)
            first, second = second, current

        return min(first, second)