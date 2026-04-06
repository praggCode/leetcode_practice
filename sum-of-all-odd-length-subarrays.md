# Sum of All Odd Length Subarrays

## Problem

Given an array of positive integers `arr`, return the **sum of all possible odd-length subarrays**.

A subarray is a **contiguous subsequence** of the array.

## Example 1

Input  
arr = [1,4,2,5,3]

Output  
58

Explanation  

Odd-length subarrays:

[1] = 1  
[4] = 4  
[2] = 2  
[5] = 5  
[3] = 3  
[1,4,2] = 7  
[4,2,5] = 11  
[2,5,3] = 10  
[1,4,2,5,3] = 15  

Total sum = 58

## Example 2

Input  
arr = [1,2]

Output  
3

Explanation  
Odd-length subarrays: [1], [2]

## Example 3

Input  
arr = [10,11,12]

Output  
66

## Constraints

- `1 <= arr.length <= 100`
- `1 <= arr[i] <= 1000`

## Solution

```python
class Solution(object):
    def sumOddLengthSubarrays(self, arr):
        n = len(arr)
        add = 0
        for start in range(n):
            for length in range(1, n - start + 1, 2):
                subset = arr[start:start + length]
                add += sum(subset)

        return add