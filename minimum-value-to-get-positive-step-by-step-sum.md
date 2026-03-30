# Minimum Value to Get Positive Step by Step Sum

## Problem

Given an array of integers `nums`, you start with an initial positive value `startValue`.

During each step, you calculate the cumulative sum of `startValue` plus elements in `nums` from left to right.

Return the **minimum positive value of `startValue`** such that the step-by-step sum is **never less than 1**.

## Example 1

Input  
nums = [-3,2,-3,4,2]

Output  
5

Explanation  
If `startValue = 4`, the running sum becomes `0` during the third step which is invalid.  
Using `startValue = 5`, the running sum always stays ≥ 1.

## Example 2

Input  
nums = [1,2]

Output  
1

Explanation  
The minimum positive start value is 1.

## Example 3

Input  
nums = [1,-2,-3]

Output  
5

## Constraints

- `1 <= nums.length <= 100`
- `-100 <= nums[i] <= 100`

## Solution

```python
class Solution(object):
    def minStartValue(self, nums):
        s = 0
        startValue = float('inf')
        for i in nums:
            s += i
            startValue = min(startValue, s)

        startValue = max(-startValue + 1, 1)
        return startValue