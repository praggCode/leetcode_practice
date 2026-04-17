# Minimum Absolute Distance Between Mirror Pairs

## Problem

You are given an integer array nums.

A mirror pair is a pair of indices (i, j) such that:

0 <= i < j < nums.length  
reverse(nums[i]) == nums[j]

Where reverse(x) means reversing the digits of x (leading zeros removed).  
Example: reverse(120) = 21.

Return the minimum absolute distance between indices of any mirror pair:  
abs(i - j)

If no mirror pair exists, return -1.

Example 1

Input: nums = [12,21,45,33,54]  
Output: 1  
Explanation: mirror pairs are (0,1) and (2,4), minimum distance is 1.

Example 2

Input: nums = [120,21]  
Output: 1  

Example 3

Input: nums = [21,120]  
Output: -1  

Constraints

1 <= nums.length <= 10^5  
1 <= nums[i] <= 10^9  

## Solution

```python
class Solution(object):
    def reverse(self, x):
        rev = 0
        while x > 0:
            rev = rev * 10 + x % 10
            x //= 10
        return rev

    def minMirrorPairDistance(self, nums):
        mpp = {}
        n = len(nums)
        ans = 10 ** 6
        for i in range(n):
            if nums[i] in mpp:
                ans = min(ans, i - mpp[nums[i]])
            mpp[self.reverse(nums[i])] = i
        return -1 if ans == 10 ** 6 else ans