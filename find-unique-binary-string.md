# Find Unique Binary String

## Problem

Given an array of strings `nums` containing `n` unique binary strings each of length `n`, return a binary string of length `n` that does **not appear** in `nums`.

If there are multiple answers, you may return **any of them**.

---

## Example 1

Input  
nums = ["01","10"]

Output  
"11"

Explanation  
"11" does not appear in nums.  
"00" would also be a valid answer.

---

## Example 2

Input  
nums = ["00","01"]

Output  
"11"

Explanation  
"11" does not appear in nums.  
"10" would also be correct.

---

## Example 3

Input  
nums = ["111","011","001"]

Output  
"101"

Explanation  
"101" does not appear in nums.  
Other valid answers include:  
"000", "010", "100", "110".

---

## Constraints

- `n == nums.length`
- `1 <= n <= 16`
- `nums[i].length == n`
- `nums[i]` contains only `'0'` or `'1'`
- All strings in `nums` are unique

---

## Solution

Idea:

Use **Cantor’s diagonalization trick**.

Construct a new string by flipping the `i-th` bit of the `i-th` string.  
This guarantees the result differs from every string in `nums`.

```python
class Solution(object):
    def findDifferentBinaryString(self, nums):
        n = len(nums)
        res = []

        for i in range(n):
            if nums[i][i] == '0':
                res.append('1')
            else:
                res.append('0')

        return "".join(res)