# Prime Number of Set Bits in Binary Representation

## Problem

Given two integers left and right, return the count of numbers in the inclusive range [left, right] having a prime number of set bits in their binary representation.

The number of set bits of an integer is the number of 1's present in its binary form.

Example

21 in binary is 10101 which has 3 set bits.

Example 1

Input: left = 6, right = 10  
Output: 4  

Explanation  
6  -> 110  (2 set bits, prime)  
7  -> 111  (3 set bits, prime)  
8  -> 1000 (1 set bit, not prime)  
9  -> 1001 (2 set bits, prime)  
10 -> 1010 (2 set bits, prime)

Example 2

Input: left = 10, right = 15  
Output: 5

Constraints

1 <= left <= right <= 10^6  
0 <= right - left <= 10^4

## Solution

```python
class Solution(object):
    def countPrimeSetBits(self, left, right):
        count = 0
        for num in range(left, right + 1):
            bits = bin(num).count('1')

            if (1 << bits) & 665772:
                count += 1

        return count