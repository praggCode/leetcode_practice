# Check If a String Contains All Binary Codes of Size K

## Problem

Given a binary string `s` and an integer `k`, return **true** if every binary code of length `k` is a substring of `s`. Otherwise, return **false**.

## Example 1

Input  
s = "00110110", k = 2

Output  
true

Explanation  
Binary codes of length 2 are:  
"00", "01", "10", "11"  
All of them appear in the string.

## Example 2

Input  
s = "0110", k = 1

Output  
true

Explanation  
Binary codes of length 1 are "0" and "1".

## Example 3

Input  
s = "0110", k = 2

Output  
false

Explanation  
The code "00" does not appear.

## Constraints

- `1 <= s.length <= 5 * 10^5`
- `s[i]` is `'0'` or `'1'`
- `1 <= k <= 20`

## Solution

```python
class Solution(object):
    def hasAllCodes(self, s, k):
        if len(s) < k:
            return False
        needed = 1 << k
        seen = set()
        for i in range(len(s) - k + 1):
            seen.add(s[i:i + k])
            if len(seen) == needed:
                return True

        return len(seen) == needed