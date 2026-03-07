# Increasing Triplet Subsequence

## Problem

Given an integer array nums, return true if there exists a triple of indices (i, j, k) such that i < j < k and nums[i] < nums[j] < nums[k]. If no such indices exist, return false.

Example 1

Input: nums = [1,2,3,4,5]  
Output: true

Example 2

Input: nums = [5,4,3,2,1]  
Output: false

Example 3

Input: nums = [2,1,5,0,4,6]  
Output: true

Constraints

1 <= nums.length <= 5 * 10^5  
-2^31 <= nums[i] <= 2^31 - 1

Follow up: Could you implement a solution that runs in O(n) time complexity and O(1) space complexity?

## Solution

```python
class Solution(object):
    def increasingTriplet(self, nums):
        first = float('inf')
        second = float('inf')

        for num in nums:
            if num <= first:
                first = num
            elif num <= second:
                second = num
            else:
                return True

        return False