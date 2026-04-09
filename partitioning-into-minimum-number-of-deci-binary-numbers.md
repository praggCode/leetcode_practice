# Partitioning Into Minimum Number Of Deci-Binary Numbers

## Problem

A decimal number is called **deci-binary** if each of its digits is either **0 or 1** without any leading zeros.

Examples of deci-binary numbers:
- 101
- 1100

Examples that are NOT deci-binary:
- 112
- 3001

Given a string `n` representing a positive decimal integer, return the **minimum number of positive deci-binary numbers** needed so that their sum equals `n`.

---

## Example 1

Input  
n = "32"

Output  
3

Explanation  
10 + 11 + 11 = 32

---

## Example 2

Input  
n = "82734"

Output  
8

---

## Example 3

Input  
n = "27346209830709182346"

Output  
9

---

## Constraints

- `1 <= n.length <= 10^5`
- `n` consists only of digits.
- `n` has no leading zeros.

---

## Solution

Key Idea:  
Each deci-binary number contributes at most **1 per digit position**.  
Therefore, the **minimum number required equals the maximum digit in the string**.

```python
class Solution(object):
    def minPartitions(self, n):
        return max(int(d) for d in n)