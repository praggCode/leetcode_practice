# Lemonade Change

## Problem

At a lemonade stand, each lemonade costs $5. Customers are standing in a queue to buy from you and order one at a time.

Each customer will pay with either a $5, $10, or $20 bill. You must provide the correct change so that each transaction results in the customer paying exactly $5.

Initially, you have no change.

Given an integer array `bills` where `bills[i]` is the bill the ith customer pays, return `true` if you can provide correct change for every customer, otherwise return `false`.

### Example 1

Input  
bills = [5,5,5,10,20]

Output  
true

Explanation  
Collect three $5 bills from the first three customers.  
Fourth customer pays $10 → give back $5.  
Fifth customer pays $20 → give back $10 and $5.

### Example 2

Input  
bills = [5,5,10,10,20]

Output  
false

Explanation  
You cannot give $15 change for the last customer.

### Constraints

- `1 <= bills.length <= 10^5`
- `bills[i] ∈ {5, 10, 20}`

## Solution

```python
class Solution(object):
    def lemonadeChange(self, bills):
        five = 0
        ten = 0
        for bill in bills:
            if bill == 5:
                five += 1
            elif bill == 10:
                if five >= 1:
                    ten += 1
                    five -= 1
                else:
                    return False
            else:
                if ten >= 1 and five >= 1:
                    ten -= 1
                    five -= 1
                elif five >= 3:
                    five -= 3
                else:
                    return False

        return True