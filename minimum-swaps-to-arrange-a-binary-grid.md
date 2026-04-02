# Minimum Swaps to Arrange a Binary Grid

## Problem

Given an `n x n` binary grid, in one step you can choose two **adjacent rows** of the grid and swap them.

A grid is considered **valid** if all the cells **above the main diagonal are zeros**.

Return the **minimum number of swaps** needed to make the grid valid, or **-1** if it cannot be done.

The main diagonal runs from cell `(1,1)` to `(n,n)`.

## Example 1

Input  
grid = [[0,0,1],[1,1,0],[1,0,0]]

Output  
3

## Example 2

Input  
grid = [[0,1,1,0],[0,1,1,0],[0,1,1,0],[0,1,1,0]]

Output  
-1

Explanation  
All rows are identical, so swapping rows does not change the grid.

## Example 3

Input  
grid = [[1,0,0],[1,1,0],[1,1,1]]

Output  
0

## Constraints

- `1 <= n <= 200`
- `grid.length == grid[i].length`
- `grid[i][j]` is either `0` or `1`

## Solution

```python
class Solution(object):
    def minSwaps(self, grid):
        n = len(grid)
        trailing = []

        for row in grid:
            count = 0
            for num in reversed(row):
                if num == 0:
                    count += 1
                else:
                    break
            trailing.append(count)
        swaps = 0

        for i in range(n):
            required = n - i - 1
            j = i
            while j < n and trailing[j] < required:
                j += 1
            if j == n:
                return -1
            while j > i:
                trailing[j], trailing[j - 1] = trailing[j - 1], trailing[j]
                swaps += 1
                j -= 1
        return swaps