# Partition Equal Subset Sum

## Problem

Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal, or false otherwise.

Example 1

Input: nums = [1,5,11,5]  
Output: true  

Explanation  
The array can be partitioned as [1, 5, 5] and [11].

Example 2

Input: nums = [1,2,3,5]  
Output: false  

Explanation  
The array cannot be partitioned into equal sum subsets.

Constraints

1 <= nums.length <= 200  
1 <= nums[i] <= 100

## Solution

```python
class Solution(object):
    def canPartition(self, nums):
        n = sum(nums)
        if n % 2 != 0:
            return False
        total = n / 2
        memo = {}
        def helper(idx, curr_sum):
            if curr_sum == total:
                return True
            if idx >= len(nums) or curr_sum > total:
                return False
            if (idx, curr_sum) in memo:
                return memo[(idx, curr_sum)]
            take = helper(idx + 1, curr_sum + nums[idx])
            non_take = helper(idx + 1, curr_sum)
            memo[(idx, curr_sum)] = take or non_take
            return memo[(idx, curr_sum)]
        return helper(0, 0)