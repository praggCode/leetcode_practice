# Largest Submatrix With Rearrangements

## Problem

You are given a binary matrix `matrix` of size `m x n`.  
You are allowed to **rearrange the columns of the matrix in any order**.

Return the **area of the largest submatrix consisting entirely of 1s** after rearranging the columns optimally.

---

## Example 1

Input  
matrix = [[0,0,1],[1,1,1],[1,0,1]]

Output  
4

Explanation  

After rearranging columns optimally:

0 0 1
1 1 1
1 1 0


The largest submatrix of 1s has area **4**.

---

## Example 2

Input  
matrix = [[1,0,1,0,1]]

Output  
3

Explanation  

By rearranging columns, we can group the `1`s together to form a submatrix with area **3**.

---

## Example 3

Input  
matrix = [[1,1,0],[1,0,1]]

Output  
2

Explanation  

Even after rearranging columns, the largest possible submatrix of 1s has area **2**.

---

## Constraints

- `m == matrix.length`
- `n == matrix[i].length`
- `1 <= m * n <= 10^5`
- `matrix[i][j]` is either `0` or `1`

---

## Solution

Idea:

1. Build heights of consecutive `1`s for each column.
2. For each row, sort the heights in descending order.
3. Compute area using `height * width`.

```python
class Solution(object):
    def largestSubmatrix(self, matrix):
        m, n = len(matrix), len(matrix[0])
        for i in range(1, m):
            for j in range(n):
                if matrix[i][j] != 0:
                    matrix[i][j] += matrix[i-1][j]
        max_area = 0
        for row in matrix:
            row.sort(reverse=True)

            for i in range(n):
                area = row[i] * (i + 1)
                max_area = max(max_area, area)

        return max_area