# Check if Binary String Has at Most One Segment of Ones

## Problem

Given a binary string `s` without leading zeros, return **true** if `s` contains **at most one contiguous segment of ones**. Otherwise, return **false**.

A segment of ones means a continuous block of `'1'` characters.

---

## Example 1

Input  
s = "1001"

Output  
false

Explanation  
The string contains two segments of ones: `"1"` and `"1"`.

---

## Example 2

Input  
s = "110"

Output  
true

Explanation  
There is only one segment of ones `"11"`.

---

## Constraints

- `1 <= s.length <= 100`
- `s[i]` is either `'0'` or `'1'`
- `s[0]` is `'1'`

---

## Solution

Idea:

Once a `'0'` appears after a segment of `'1'`, no more `'1'` should appear.

```python
class Solution(object):
    def checkOnesSegment(self, s):
        seen_zero = False
        for ch in s:
            if ch == '0':
                seen_zero = True
            elif seen_zero:
                return False
        return True