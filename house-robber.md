# House Robber

## Problem

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed.

The only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.

Example 1

Input: nums = [1,2,3,1]  
Output: 4  
Explanation: Rob house 1 and house 3.

Example 2

Input: nums = [2,7,9,3,1]  
Output: 12  
Explanation: Rob house 1, house 3 and house 5.

Constraints

1 <= nums.length <= 100  
0 <= nums[i] <= 400

## Solution

```python
class Solution(object):
    def rob(self, nums):
        memo = {}

        def helper(idx):
            if idx in memo:
                return memo[idx]

            if idx >= len(nums):
                return 0

            curr_rob = nums[idx] + helper(idx + 2)
            skip_rob = helper(idx + 1)

            memo[idx] = max(curr_rob, skip_rob)
            return memo[idx]

        return helper(0)