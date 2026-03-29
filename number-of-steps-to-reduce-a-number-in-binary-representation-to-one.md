# Number of Steps to Reduce a Number in Binary Representation to One

## Problem

Given the binary representation of an integer as a string `s`, return the number of steps required to reduce it to `1` using the following rules:

- If the current number is **even**, divide it by `2`.
- If the current number is **odd**, add `1` to it.

It is guaranteed that the number can always be reduced to `1`.

## Example 1

Input  
s = "1101"

Output  
6

Explanation  
"1101" represents decimal 13.

Step 1: 13 is odd → add 1 → 14  
Step 2: 14 is even → divide by 2 → 7  
Step 3: 7 is odd → add 1 → 8  
Step 4: 8 is even → divide by 2 → 4  
Step 5: 4 is even → divide by 2 → 2  
Step 6: 2 is even → divide by 2 → 1  

## Example 2

Input  
s = "10"

Output  
1

Explanation  
"10" represents decimal 2.

Step 1: divide by 2 → 1

## Example 3

Input  
s = "1"

Output  
0

## Constraints

- 1 <= s.length <= 500  
- s consists only of `'0'` and `'1'`  
- s[0] == `'1'`

## Solution

```python
class Solution(object):
    def numSteps(self, s):
        steps = 0
        carry = 0
        for i in range(len(s) - 1, 0, -1):
            bit = int(s[i])
            if bit + carry == 1:
                steps += 2
                carry = 1
            else:
                steps += 1

        return steps + carry