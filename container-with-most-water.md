# Container With Most Water

## Problem

You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.

Example 1

Input: height = [1,8,6,2,5,4,8,3,7]  
Output: 49  
Explanation: The maximum area of water the container can contain is 49.

## Solution

```python
class Solution(object):
    def maxArea(self, height):
        left, right = 0, len(height) - 1
        max_water = 0

        while left < right:
            width = right - left
            current_height = min(height[left], height[right])
            max_water = max(max_water, current_height * width)

            if height[left] < height[right]:
                left += 1
            else:
                right -= 1

        return max_water