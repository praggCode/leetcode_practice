# Koko Eating Bananas

## Problem

Koko loves to eat bananas. There are `n` piles of bananas, and the `i-th` pile has `piles[i]` bananas. The guards will return in `h` hours.

Koko can choose her eating speed `k` bananas per hour. Each hour she chooses one pile and eats `k` bananas from it. If the pile has fewer than `k` bananas, she eats all the bananas in that pile and does not eat anything else that hour.

Koko wants to eat as slowly as possible but still finish all the bananas before the guards return.

Return the minimum integer `k` such that she can eat all the bananas within `h` hours.

## Example 1

Input  
piles = [3,6,7,11], h = 8  

Output  
4

## Example 2

Input  
piles = [30,11,23,4,20], h = 5  

Output  
30

## Example 3

Input  
piles = [30,11,23,4,20], h = 6  

Output  
23

## Constraints

- `1 <= piles.length <= 10^4`
- `piles.length <= h <= 10^9`
- `1 <= piles[i] <= 10^9`

## Solution

```python
class Solution(object):
    def minEatingSpeed(self, piles, h):
        low, high = 1, max(piles)

        def canEatAll(k):
            totalHours = 0
            for bananas in piles:
                totalHours += (bananas + k - 1) // k
            return totalHours <= h

        while low < high:
            mid = (low + high) // 2
            if canEatAll(mid):
                high = mid
            else:
                low = mid + 1
        return low