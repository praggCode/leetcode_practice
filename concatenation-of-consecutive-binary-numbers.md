# Concatenation of Consecutive Binary Numbers

## Problem

Given an integer `n`, return the decimal value of the binary string formed by concatenating the binary representations of numbers from `1` to `n` in order.

Return the result modulo \(10^9 + 7\).

---

## Example 1

Input  
n = 1

Output  
1

Explanation  
Binary of 1 → "1"  
Decimal value = 1

---

## Example 2

Input  
n = 3

Output  
27

Explanation  

Binary representations:

1 → "1"  
2 → "10"  
3 → "11"

Concatenated string:

"11011"

Decimal value = 27

---

## Example 3

Input  
n = 12

Output  
505379714

Explanation  

Concatenated binary string:

1101110010111011110001001101010111100

Decimal value = 118505380540

After modulo \(10^9 + 7\):

505379714

---

## Constraints

- `1 <= n <= 10^5`

---

## Solution

```python
class Solution(object):
    def concatenatedBinary(self, n):
        MOD = 10**9 + 7
        ans = 0
        length = 0
        for i in range(1, n + 1):
            if (i & (i - 1)) == 0:
                length += 1
            ans = ((ans << length) + i) % MOD
            
        return ans