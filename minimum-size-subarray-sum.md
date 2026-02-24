# Minimum Size Subarray Sum

## Problem

Given an array of positive integers nums and a positive integer target, return the minimal length of a subarray whose sum is greater than or equal to target. If there is no such subarray, return 0 instead.

Example 1

Input: target = 7, nums = [2,3,1,2,4,3]  
Output: 2  
Explanation: The subarray [4,3] has the minimal length.

Example 2

Input: target = 4, nums = [1,4,4]  
Output: 1

Example 3

Input: target = 11, nums = [1,1,1,1,1,1,1,1]  
Output: 0

Constraints

1 <= target <= 10^9  
1 <= nums.length <= 10^5  
1 <= nums[i] <= 10^4

Follow up: If you have figured out the O(n) solution, try coding another solution with time complexity O(n log n).

## Solution

```python
class Solution(object):
    def minSubArrayLen(self, target, nums):
        min_len = float("inf")
        left = 0
        total = 0

        for right in range(len(nums)):
            total += nums[right]

            while total >= target:
                min_len = min(min_len, right - left + 1)
                total -= nums[left]
                left += 1

        if min_len == float("inf"):
            return 0

        return min_len