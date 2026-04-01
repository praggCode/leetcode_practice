# Water Bottles

## Problem

There are `numBottles` water bottles that are initially full of water. You can exchange `numExchange` empty water bottles for one full water bottle.

Drinking a full water bottle turns it into an empty bottle.

Given two integers `numBottles` and `numExchange`, return the maximum number of water bottles you can drink.

## Example 1

Input  
numBottles = 9  
numExchange = 3  

Output  
13  

Explanation  
You can exchange 3 empty bottles for 1 full bottle.

Total bottles drunk:  
9 + 3 + 1 = 13

## Example 2

Input  
numBottles = 15  
numExchange = 4  

Output  
19  

Explanation  
You can exchange 4 empty bottles for 1 full bottle.

Total bottles drunk:  
15 + 3 + 1 = 19

## Constraints

- `1 <= numBottles <= 100`
- `2 <= numExchange <= 100`

## Solution

```python
class Solution(object):
    def numWaterBottles(self, numBottles, numExchange):
        total = numBottles
        while numBottles >= numExchange:
            newBottles = numBottles // numExchange
            remBottles = numBottles % numExchange

            total += newBottles
            numBottles = newBottles + remBottles

        return total