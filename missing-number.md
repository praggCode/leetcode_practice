# Missing Number

## Problem

Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

Example 1

Input: nums = [3,0,1]  
Output: 2

Explanation  
n = 3 since there are 3 numbers, so all numbers are in the range [0,3].  
2 is the missing number since it does not appear in nums.

Example 2

Input: nums = [0,1]  
Output: 2

Example 3

Input: nums = [9,6,4,2,3,5,7,0,1]  
Output: 8

Constraints

n == nums.length  
1 <= n <= 10^4  
0 <= nums[i] <= n  
All the numbers of nums are unique.

## Solution

```python
class Solution(object):
    def missingNumber(self, nums):
        nums.sort()
        nums.append(0)

        for i in range(len(nums) + 1):
            if i != nums[i]:
                return i