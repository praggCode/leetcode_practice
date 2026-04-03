# Find Kth Bit in Nth Binary String

## Problem

Given two positive integers `n` and `k`, the binary string `S_n` is defined as:

- `S1 = "0"`
- `S_i = S_{i-1} + "1" + reverse(invert(S_{i-1}))` for `i > 1`

Where:

- `+` means concatenation
- `reverse(x)` returns the reversed string
- `invert(x)` flips all bits (`0 → 1`, `1 → 0`)

The first few strings are:

S1 = "0"  
S2 = "011"  
S3 = "0111001"  
S4 = "011100110110001"

Return the **k-th bit** of `S_n`.

## Example 1

Input  
n = 3  
k = 1  

Output  
"0"

Explanation  
S3 = "0111001"  
The 1st bit is "0".

## Example 2

Input  
n = 4  
k = 11  

Output  
"1"

Explanation  
S4 = "011100110110001"  
The 11th bit is "1".

## Constraints

- `1 <= n <= 20`
- `1 <= k <= 2^n - 1`

## Solution

```python
class Solution(object):
    def findKthBit(self, n, k):
        if n == 1:
            return "0"
        mid = 2 ** (n - 1)
        if k == mid:
            return "1"
        elif k < mid:
            return self.findKthBit(n - 1, k)
        else:
            mirrored = 2 ** n - k
            bit = self.findKthBit(n - 1, mirrored)
            return "1" if bit == "0" else "0"