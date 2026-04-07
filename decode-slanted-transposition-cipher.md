# Decode Slanted Transposition Cipher

## Problem

A string `originalText` is encoded using a **slanted transposition cipher** into `encodedText` using a matrix with a fixed number of rows `rows`.

Encoding process:

1. `originalText` is placed diagonally from **top-left to bottom-right** in the matrix.
2. Empty cells are filled with spaces `' '`.
3. The number of columns is chosen so the last column is not empty.
4. `encodedText` is created by reading the matrix **row by row**.

Given `encodedText` and `rows`, return the decoded **originalText**.

Note:  
`originalText` does not contain trailing spaces.

---

## Example 1

Input  
encodedText = "ch   ie   pr"  
rows = 3  

Output  
cipher

---

## Example 2

Input  
encodedText = "iveo    eed   l te   olc"  
rows = 4  

Output  
i love leetcode

---

## Example 3

Input  
encodedText = "coding"  
rows = 1  

Output  
coding

---

## Constraints

- `0 <= encodedText.length <= 10^6`
- `encodedText` contains lowercase letters and spaces
- `1 <= rows <= 1000`
- There is exactly **one valid originalText**

---

## Solution

Idea:

1. Compute number of columns `cols = len(encodedText) / rows`
2. Build the matrix row-wise from `encodedText`
3. Read characters diagonally
4. Remove trailing spaces

```python
class Solution(object):
    def decodeCiphertext(self, encodedText, rows):
        if rows == 1:
            return encodedText

        n = len(encodedText)
        cols = n // rows
        matrix = []
        idx = 0
        for r in range(rows):
            matrix.append(list(encodedText[idx:idx+cols]))
            idx += cols

        result = []
        for start_col in range(cols):
            r, c = 0, start_col
            while r < rows and c < cols:
                result.append(matrix[r][c])
                r += 1
                c += 1

        return ''.join(result).rstrip()