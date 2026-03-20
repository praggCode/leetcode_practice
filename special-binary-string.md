# Special Binary String

## Problem

Special binary strings are binary strings with the following two properties:

- The number of `0`s is equal to the number of `1`s.
- Every prefix of the binary string has at least as many `1`s as `0`s.

You are given a special binary string `s`.

A move consists of choosing two consecutive, non-empty, special substrings of `s` and swapping them.

Return the lexicographically largest resulting string possible after performing any number of swaps.

### Example 1

Input: s = "11011000"  
Output: "11100100"

Explanation:  
The substrings `"10"` and `"1100"` can be swapped to produce the largest possible string.

### Example 2

Input: s = "10"  
Output: "10"

### Constraints

- `1 <= s.length <= 50`
- `s[i]` is either `'0'` or `'1'`
- `s` is guaranteed to be a special binary string.

## Solution

```python
class Solution(object):
    def makeLargestSpecial(self, s):
        if len(s) <= 2:
            return s
        count = 0
        start = 0
        result = []
        for i in range(len(s)):
            if s[i] == '1':
                count += 1
            else:
                count -= 1

            if count == 0:
                inner = self.makeLargestSpecial(s[start + 1:i])
                result.append("1" + inner + "0")
                start = i + 1

        result.sort(reverse=True)
        return "".join(result)