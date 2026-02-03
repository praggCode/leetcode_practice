# Reverse Integer

## Problem

Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-2^31, 2^31 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

Example 1

Input: x = 123  
Output: 321

Example 2

Input: x = -123  
Output: -321

Example 3

Input: x = 120  
Output: 21

Constraints

-2^31 <= x <= 2^31 - 1

## Solution

```python
class Solution(object):
    def reverse(self, x):
        y = []
        if -(2**31) <= x <= (2**31) - 1:
            is_negative = x < 0
            if is_negative:
                x = -x
            while x > 0:
                a = x % 10
                y.append(a)
                x = x // 10
            num = 0
            n = len(y)
            for i in range(n):
                num += y[i] * (10 ** (n - 1 - i))
            if is_negative:
                num = -num
            if -(2**31) <= num <= (2**31) - 1:
                return num
            else:
                return 0
        else:
            return 0