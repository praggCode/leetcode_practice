# Count Binary Substrings

## Problem

Given a binary string s, return the number of non-empty substrings that have the same number of 0's and 1's, and all the 0's and all the 1's in these substrings are grouped consecutively.

Substrings that occur multiple times are counted the number of times they occur.

Example 1

Input: s = "00110011"  
Output: 6  

Explanation  
The substrings are: "0011", "01", "1100", "10", "0011", "01".

Example 2

Input: s = "10101"  
Output: 4  

Explanation  
The substrings are: "10", "01", "10", "01".

Constraints

1 <= s.length <= 10^5  
s[i] is either '0' or '1'

## Solution

```python
class Solution(object):
    def countBinarySubstrings(self, s):
        prev_group = 0
        curr_group = 1
        result = 0
        for i in range(1, len(s)):
            if s[i] == s[i - 1]:
                curr_group += 1
            else:
                result += min(prev_group, curr_group)
                prev_group = curr_group
                curr_group = 1
        result += min(prev_group, curr_group)
        return result