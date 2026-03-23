# Binary Gap

## Problem

Given a positive integer `n`, find and return the longest distance between any two adjacent `1`s in the binary representation of `n`.

Two `1`s are adjacent if there are only `0`s separating them.  
The distance between two `1`s is the absolute difference between their bit positions.

If there are no two adjacent `1`s, return `0`.

### Example 1

Input: n = 22  
Output: 2  

Explanation  
22 in binary is `10110`.  
Distances between adjacent `1`s are `2` and `1`.  
The maximum distance is `2`.

### Example 2

Input: n = 8  
Output: 0  

Explanation  
8 in binary is `1000`.  
There are no adjacent `1`s.

### Example 3

Input: n = 5  
Output: 2  

Explanation  
5 in binary is `101`.

### Constraints

- `1 <= n <= 10^9`

## Solution

```python
class Solution(object):
    def binaryGap(self, n):
        last_position = -1
        max_distance = 0
        current_position = 0
        while n > 0:
            if n & 1:
                if last_position != -1:
                    max_distance = max(max_distance, current_position - last_position)
                last_position = current_position
            n >>= 1
            current_position += 1
        return max_distance