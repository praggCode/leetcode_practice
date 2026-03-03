# Longest Increasing Subsequence

## Problem

Given an integer array nums, return the length of the longest strictly increasing subsequence.

Example 1

Input: nums = [10,9,2,5,3,7,101,18]  
Output: 4  
Explanation: The longest increasing subsequence is [2,3,7,101].

Example 2

Input: nums = [0,1,0,3,2,3]  
Output: 4

Example 3

Input: nums = [7,7,7,7,7,7,7]  
Output: 1

Constraints

1 <= nums.length <= 2500  
-10^4 <= nums[i] <= 10^4

## Solution

```python
class Solution(object):
    def lengthOfLIS(self, nums):
        if not nums:
            return 0

        arr = [1] * len(nums)

        for i in range(1, len(nums)):
            for j in range(i):
                if nums[i] > nums[j]:
                    arr[i] = max(arr[i], arr[j] + 1)

        return max(arr)