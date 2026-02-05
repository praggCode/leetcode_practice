# Integer to Roman

## Problem

Seven different symbols represent Roman numerals with the following values:

Symbol   Value  
I        1  
V        5  
X        10  
L        50  
C        100  
D        500  
M        1000  

Roman numerals are formed by appending the conversions of decimal place values from highest to lowest.

Rules:

If the value does not start with 4 or 9, select the symbol of the maximal value that can be subtracted from the input, append that symbol to the result, subtract its value, and convert the remainder to a Roman numeral.

If the value starts with 4 or 9 use the subtractive form representing one symbol subtracted from the following symbol.

Subtractive forms used are:
4 (IV), 9 (IX), 40 (XL), 90 (XC), 400 (CD), 900 (CM).

Only powers of 10 (I, X, C, M) can be appended consecutively at most 3 times.

Given an integer, convert it to a Roman numeral.

Example 1

Input: num = 3749  
Output: "MMMDCCXLIX"

Example 2

Input: num = 58  
Output: "LVIII"

Example 3

Input: num = 1994  
Output: "MCMXCIV"

## Solution

```python
class Solution(object):
    def intToRoman(self, num):
        roman = {
            1000: "M", 900: "CM", 500: "D", 400: "CD",
            100: "C", 90: "XC", 50: "L", 40: "XL",
            10: "X", 9: "IX", 5: "V", 4: "IV", 1: "I"
        }

        result = ""

        for value in sorted(roman.keys(), reverse=True):
            symbol = roman[value]

            while num >= value:
                result += symbol
                num -= value

        return result