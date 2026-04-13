# Get Biggest Three Rhombus Sums in a Grid

## Problem

You are given an `m x n` integer matrix `grid`.

A **rhombus sum** is the sum of the elements that form the **border of a rhombus shape** in the grid.

The rhombus must look like a **square rotated 45°**, with each corner located at a grid cell.

A rhombus can also have **area 0**, meaning it consists of a **single cell**.

Return the **three largest distinct rhombus sums** in **descending order**.  
If there are fewer than three distinct sums, return all of them.

---

## Example 1

Input  
grid = [[3,4,5,1,3],
        [3,3,4,2,3],
        [20,30,200,40,10],
        [1,5,5,4,1],
        [4,3,2,2,5]]

Output  
[228,216,211]

Explanation  

Three largest rhombus sums:

- 20 + 3 + 200 + 5 = 228  
- 200 + 2 + 10 + 4 = 216  
- 5 + 200 + 4 + 2 = 211  

---

## Example 2

Input  
grid = [[1,2,3],
        [4,5,6],
        [7,8,9]]

Output  
[20,9,8]

Explanation  

Rhombus sums include:

- 4 + 2 + 6 + 8 = 20  
- 9 (single cell)  
- 8 (single cell)

---

## Example 3

Input  
grid = [[7,7,7]]

Output  
[7]

Explanation  
All possible rhombus sums are the same.

---

## Constraints

- `m == grid.length`
- `n == grid[i].length`
- `1 <= m, n <= 50`
- `1 <= grid[i][j] <= 10^5`

---

## Solution

Idea:

1. Treat each cell as the **top of a rhombus**.
2. Expand the rhombus layer by layer.
3. Compute the **border sum**.
4. Store sums in a **set** to keep them distinct.
5. Return the **top 3 largest values**.

```python
class Solution(object):
    def getBiggestThree(self, grid):
        m, n = len(grid), len(grid[0])
        res = set()

        for i in range(m):
            for j in range(n):
                res.add(grid[i][j])

                k = 1
                while True:
                    if i + 2*k >= m or j - k < 0 or j + k >= n:
                        break

                    s = 0

                    x, y = i, j
                    for d in range(k):
                        s += grid[x+d][y+d]

                    x, y = i+k, j+k
                    for d in range(k):
                        s += grid[x+d][y-d]

                    x, y = i+2*k, j
                    for d in range(k):
                        s += grid[x-d][y-d]

                    x, y = i+k, j-k
                    for d in range(k):
                        s += grid[x-d][y+d]

                    res.add(s)
                    k += 1

        return sorted(res, reverse=True)[:3]