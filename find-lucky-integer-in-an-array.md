# Find Lucky Integer in an Array

## Problem

Given an array of integers `arr`, a lucky integer is an integer whose **frequency in the array equals its value**.

Return the **largest lucky integer** in the array. If there is no lucky integer, return `-1`.

## Example 1

Input  
arr = [2,2,3,4]

Output  
2

Explanation  
The only lucky number is 2 because its frequency is 2.

## Example 2

Input  
arr = [1,2,2,3,3,3]

Output  
3

Explanation  
1, 2, and 3 are lucky numbers. The largest is 3.

## Example 3

Input  
arr = [2,2,2,3,3]

Output  
-1

Explanation  
There are no lucky numbers.

## Constraints

- 1 <= arr.length <= 500  
- 1 <= arr[i] <= 500  

## Solution

```python
class Solution(object):
    def findLucky(self, arr):
        from collections import Counter
        freq = Counter(arr)
        ans = -1
        for num in freq:
            if freq[num] == num:
                ans = max(ans, num)

        return ans