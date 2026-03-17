# Find Pivot Index

## Problem

Given an array of integers nums, calculate the pivot index of this array.

The pivot index is the index where the sum of all the numbers strictly to the left of the index is equal to the sum of all the numbers strictly to the right.

If the index is on the left edge, the left sum is 0 because there are no elements to the left. This also applies to the right edge.

Return the leftmost pivot index. If no such index exists, return -1.

Example 1

Input: nums = [1,7,3,6,5,6]  
Output: 3  

Explanation  
Left sum = 1 + 7 + 3 = 11  
Right sum = 5 + 6 = 11

Example 2

Input: nums = [1,2,3]  
Output: -1

Example 3

Input: nums = [2,1,-1]  
Output: 0

Constraints

1 <= nums.length <= 10^4  
-1000 <= nums[i] <= 1000

## Solution

```python
class Solution(object):
    def pivotIndex(self, nums):
        n = len(nums)
        pre = [0] * (n + 1)
        for i in range(1, n + 1):
            pre[i] = pre[i - 1] + nums[i - 1]

        for i in range(len(pre) - 1):
            if pre[i] == pre[n] - pre[i + 1]:
                return i

        return -1