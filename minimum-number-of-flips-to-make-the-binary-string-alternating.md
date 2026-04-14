# Minimum Number of Flips to Make the Binary String Alternating

## Problem

You are given a binary string `s`. You can perform two types of operations:

Type-1  
Remove the character at the start of the string and append it to the end.

Type-2  
Pick any character and flip it (`0 → 1` or `1 → 0`).

Return the **minimum number of type-2 operations** required to make the string **alternating**.

A string is alternating if **no two adjacent characters are equal**.

Examples of alternating strings:

010  
1010

Non-alternating example:

0100

---

## Example 1

Input  
s = "111000"

Output  
2

Explanation  

Rotate twice:

111000 → 110001 → 100011  

Then flip characters to get:

101010

---

## Example 2

Input  
s = "010"

Output  
0

Explanation  

Already alternating.

---

## Example 3

Input  
s = "1110"

Output  
1

Explanation  

Flip one character to obtain:

1010

---

## Constraints

- `1 <= s.length <= 10^5`
- `s[i]` is either `'0'` or `'1'`

---

## Solution

Idea:

1. Duplicate the string to simulate rotations.
2. Compare with two alternating patterns:
   - `010101...`
   - `101010...`
3. Use a **sliding window of size n** to compute the minimum flips.

```python
class Solution(object):
    def minFlips(self, s):
        n = len(s)
        s2 = s + s
        alt1 = ""
        alt2 = ""
        for i in range(2 * n):
            if i % 2 == 0:
                alt1 += "0"
                alt2 += "1"
            else:
                alt1 += "1"
                alt2 += "0"

        diff1 = diff2 = 0
        left = 0
        ans = float('inf')

        for right in range(2 * n):
            if s2[right] != alt1[right]:
                diff1 += 1
            if s2[right] != alt2[right]:
                diff2 += 1
            if right - left + 1 > n:
                if s2[left] != alt1[left]:
                    diff1 -= 1
                if s2[left] != alt2[left]:
                    diff2 -= 1
                left += 1

            if right - left + 1 == n:
                ans = min(ans, diff1, diff2)

        return ans