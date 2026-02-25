# House Robber II

## Problem

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses are arranged in a circle, meaning the first house is the neighbor of the last one.

Adjacent houses have a security system connected, and it will automatically contact the police if two adjacent houses are robbed on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob without alerting the police.

Example 1

Input: nums = [2,3,2]  
Output: 3  
Explanation: You cannot rob house 1 and house 3 because they are adjacent.

Example 2

Input: nums = [1,2,3,1]  
Output: 4  
Explanation: Rob house 1 and house 3.

Example 3

Input: nums = [1,2,3]  
Output: 3

Constraints

1 <= nums.length <= 100  
0 <= nums[i] <= 1000

## Solution

```python
class Solution(object):
    def rob(self, nums):
        if len(nums) == 1:
            return nums[0]

        def helper(nums, idx, memo):
            if idx in memo:
                return memo[idx]

            if idx >= len(nums):
                return 0

            rob = nums[idx] + helper(nums, idx + 2, memo)
            skip = helper(nums, idx + 1, memo)

            memo[idx] = max(rob, skip)
            return memo[idx]

        return max(helper(nums[1:], 0, {}), helper(nums[:-1], 0, {}))