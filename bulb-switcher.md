# Bulb Switcher

## Problem

There are n bulbs that are initially off. You first turn on all the bulbs, then you turn off every second bulb.

On the third round, you toggle every third bulb (turning on if it is off or turning off if it is on). For the ith round, you toggle every i bulb. For the nth round, you only toggle the last bulb.

Return the number of bulbs that are on after n rounds.

Example 1

Input: n = 3  
Output: 1

Explanation  
Initially: [off, off, off]  
After round 1: [on, on, on]  
After round 2: [on, off, on]  
After round 3: [on, off, off]

Example 2

Input: n = 0  
Output: 0

Example 3

Input: n = 1  
Output: 1

Constraints

0 <= n <= 10^9

## Solution

```python
class Solution(object):
    def bulbSwitch(self, n):
        count = 0
        i = 1
        while i * i <= n:
            count += 1
            i += 1

        return count