# Special Positions in a Binary Matrix

## Problem

Given an `m x n` binary matrix `mat`, return the number of **special positions**.

A position `(i, j)` is special if:

- `mat[i][j] == 1`
- All other elements in **row i** are `0`
- All other elements in **column j** are `0`

Rows and columns are **0-indexed**.

## Example 1

Input  
mat = [[1,0,0],
       [0,0,1],
       [1,0,0]]

Output  
1

Explanation  
Position `(1,2)` is special.

## Example 2

Input  
mat = [[1,0,0],
       [0,1,0],
       [0,0,1]]

Output  
3

Explanation  
Positions `(0,0)`, `(1,1)`, and `(2,2)` are special.

## Constraints

- `1 <= m, n <= 100`
- `mat[i][j]` is either `0` or `1`

## Solution

```python
class Solution(object):
    def numSpecial(self, mat):
        m = len(mat)
        n = len(mat[0])
        row = [0] * m
        col = [0] * n
        for i in range(m):
            for j in range(n):
                if mat[i][j] == 1:
                    row[i] += 1
                    col[j] += 1
        count = 0
        for i in range(m):
            for j in range(n):
                if mat[i][j] == 1 and row[i] == 1 and col[j] == 1:
                    count += 1

        return count