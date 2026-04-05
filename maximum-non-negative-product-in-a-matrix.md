# Maximum Non Negative Product in a Matrix

## Problem

You are given an `m x n` matrix `grid`. Initially, you start at the **top-left corner (0,0)** and you can only move **right** or **down**.

Among all possible paths from `(0,0)` to `(m-1,n-1)`, find the path with the **maximum non-negative product**.

The product of a path is the multiplication of all values in the cells visited along the path.

Return the **maximum non-negative product modulo (10^9 + 7)**.  
If the maximum product is negative, return **-1**.

## Example 1

Input  
grid = [[-1,-2,-3],
        [-2,-3,-3],
        [-3,-3,-2]]

Output  
-1

Explanation  
No path produces a non-negative product.

## Example 2

Input  
grid = [[1,-2,1],
        [1,-2,1],
        [3,-4,1]]

Output  
8

Explanation  
Path product = 1 × 1 × -2 × -4 × 1 = 8.

## Example 3

Input  
grid = [[1,3],
        [0,-4]]

Output  
0

Explanation  
Path product = 1 × 0 × -4 = 0.

## Constraints

- `1 <= m, n <= 15`
- `-4 <= grid[i][j] <= 4`

## Solution

```python
class Solution(object):
    def maxProductPath(self, grid):
        m, n = len(grid), len(grid[0])
        MOD = 10**9 + 7

        max_dp = [[0]*n for _ in range(m)]
        min_dp = [[0]*n for _ in range(m)]

        max_dp[0][0] = min_dp[0][0] = grid[0][0]

        for i in range(1, m):
            val = grid[i][0]
            max_dp[i][0] = max_dp[i-1][0] * val
            min_dp[i][0] = max_dp[i][0]

        for j in range(1, n):
            val = grid[0][j]
            max_dp[0][j] = max_dp[0][j-1] * val
            min_dp[0][j] = max_dp[0][j]

        for i in range(1, m):
            for j in range(1, n):
                val = grid[i][j]

                candidates = [
                    max_dp[i-1][j] * val,
                    min_dp[i-1][j] * val,
                    max_dp[i][j-1] * val,
                    min_dp[i][j-1] * val
                ]

                max_dp[i][j] = max(candidates)
                min_dp[i][j] = min(candidates)

        res = max_dp[m-1][n-1]
        if res < 0:
            return -1

        return res % MOD