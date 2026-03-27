# Longest Common Subsequence

## Problem

Given two strings `text1` and `text2`, return the length of their **longest common subsequence**. If there is no common subsequence, return `0`.

A subsequence of a string is a new string generated from the original string with some characters deleted without changing the relative order of the remaining characters.

Example: `"ace"` is a subsequence of `"abcde"`.

A **common subsequence** of two strings is a subsequence that appears in both strings.

## Example 1

Input  
text1 = "abcde"  
text2 = "ace"

Output  
3

Explanation  
The longest common subsequence is `"ace"`.

## Example 2

Input  
text1 = "abc"  
text2 = "abc"

Output  
3

Explanation  
The longest common subsequence is `"abc"`.

## Example 3

Input  
text1 = "abc"  
text2 = "def"

Output  
0

Explanation  
There is no common subsequence.

## Constraints

- `1 <= text1.length, text2.length <= 1000`
- `text1` and `text2` consist only of lowercase English characters.

## Solution

```python
class Solution(object):
    def longestCommonSubsequence(self, text1, text2):
        memo = {}

        def helper(i, j):
            if i >= len(text1) or j >= len(text2):
                return 0
            if (i, j) in memo:
                return memo[(i, j)]
            if text1[i] == text2[j]:
                memo[(i, j)] = 1 + helper(i + 1, j + 1)
            else:
                a = helper(i, j + 1)
                b = helper(i + 1, j)
                memo[(i, j)] = max(a, b)
            return memo[(i, j)]

        return helper(0, 0)