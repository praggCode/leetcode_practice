# N-th Tribonacci Number

## Problem

The Tribonacci sequence Tₙ is defined as follows:

T₀ = 0  
T₁ = 1  
T₂ = 1  

For n ≥ 0:

Tₙ₊₃ = Tₙ + Tₙ₊₁ + Tₙ₊₂

Given an integer `n`, return the value of `Tₙ`.

## Example 1

Input  
n = 4

Output  
4

Explanation  
T₃ = 0 + 1 + 1 = 2  
T₄ = 1 + 1 + 2 = 4

## Example 2

Input  
n = 25

Output  
1389537

## Constraints

- 0 <= n <= 37  
- The answer fits in a 32-bit integer.

## Solution

```python
class Solution(object):
    def tribonacci(self, n):
        l = [0] * (n + 1)
        if n == 0:
            return 0
        if n == 1:
            return 1
        if n == 2:
            return 1

        l[0] = 0
        l[1] = 1
        l[2] = 1

        for i in range(3, n + 1):
            l[i] = l[i - 1] + l[i - 2] + l[i - 3]

        return l[-1]