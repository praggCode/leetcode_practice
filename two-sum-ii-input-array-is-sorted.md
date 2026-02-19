# Two Sum II - Input Array Is Sorted

## Problem

Given a 1-indexed array of integers numbers that is already sorted in non-decreasing order, find two numbers such that they add up to a specific target number.

Let these two numbers be numbers[index1] and numbers[index2] where  
1 <= index1 < index2 <= numbers.length.

Return the indices of the two numbers index1 and index2, each incremented by one, as an integer array [index1, index2].

There is exactly one solution and you may not use the same element twice.

Your solution must use only constant extra space.

Example 1

Input: numbers = [2,7,11,15], target = 9  
Output: [1,2]

Example 2

Input: numbers = [2,3,4], target = 6  
Output: [1,3]

Example 3

Input: numbers = [-1,0], target = -1  
Output: [1,2]

Constraints

2 <= numbers.length <= 3 * 10^4  
-1000 <= numbers[i] <= 1000  
numbers is sorted in non-decreasing order.  
-1000 <= target <= 1000

## Solution

```python
class Solution(object):
    def twoSum(self, numbers, target):
        left = 0
        right = len(numbers) - 1

        while left < right:
            current_sum = numbers[left] + numbers[right]

            if current_sum == target:
                return [left + 1, right + 1]

            elif current_sum < target:
                left += 1
            else:
                right -= 1