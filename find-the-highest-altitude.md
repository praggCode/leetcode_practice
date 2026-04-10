# Find the Highest Altitude

## Problem

There is a biker going on a road trip. The road trip consists of `n + 1` points at different altitudes.

The biker starts at point `0` with altitude `0`.

You are given an integer array `gain` of length `n` where:

gain[i] = net altitude change between point `i` and `i + 1`.

Return the **highest altitude** reached during the trip.

---

## Example 1

Input  
gain = [-5,1,5,0,-7]

Output  
1

Explanation  

Altitudes:

0 → start  
0 - 5 = -5  
-5 + 1 = -4  
-4 + 5 = 1  
1 + 0 = 1  
1 - 7 = -6  

Altitudes array = `[0, -5, -4, 1, 1, -6]`

Highest altitude = **1**

---

## Example 2

Input  
gain = [-4,-3,-2,-1,4,3,2]

Output  
0

Explanation  

Altitudes:

`[0, -4, -7, -9, -10, -6, -3, -1]`

Highest altitude = **0**

---

## Constraints

- `n == gain.length`
- `1 <= n <= 100`
- `-100 <= gain[i] <= 100`

---

## Solution

```python
class Solution:
    def largestAltitude(self, gain):
        altitudes = [0]
        alt = 0
        for i in range(len(gain)):
            alt += gain[i]
            altitudes.append(alt)
        return max(altitudes)