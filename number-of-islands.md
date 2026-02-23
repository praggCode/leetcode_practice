# Number of Islands

## Problem

Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.

An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are surrounded by water.

Example 1

Input:  
grid = [
["1","1","1","1","0"],
["1","1","0","1","0"],
["1","1","0","0","0"],
["0","0","0","0","0"]
]

Output: 1

Example 2

Input:  
grid = [
["1","1","0","0","0"],
["1","1","0","0","0"],
["0","0","1","0","0"],
["0","0","0","1","1"]
]

Output: 3

Constraints

m == grid.length  
n == grid[i].length  
1 <= m, n <= 300  
grid[i][j] is '0' or '1'

## Solution

```python
from collections import deque

class Solution(object):
    def numIslands(self, grid):
        if not grid:
            return 0

        rows, cols = len(grid), len(grid[0])
        directions = [(1,0), (-1,0), (0,1), (0,-1)]
        ans = 0

        for i in range(rows):
            for j in range(cols):
                if grid[i][j] == "1":
                    ans += 1
                    queue = deque()
                    queue.append((i, j))
                    grid[i][j] = "0"

                    while queue:
                        x, y = queue.popleft()

                        for dx, dy in directions:
                            nx, ny = x + dx, y + dy

                            if 0 <= nx < rows and 0 <= ny < cols and grid[nx][ny] == "1":
                                queue.append((nx, ny))
                                grid[nx][ny] = "0"

        return ans