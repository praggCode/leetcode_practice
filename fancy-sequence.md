# Fancy Sequence

## Problem

Write an API that generates fancy sequences using the append, addAll, and multAll operations.

Implement the Fancy class:

Fancy()  
Initializes the object with an empty sequence.

append(val)  
Appends an integer `val` to the end of the sequence.

addAll(inc)  
Increments all existing values in the sequence by `inc`.

multAll(m)  
Multiplies all existing values in the sequence by `m`.

getIndex(idx)  
Gets the current value at index `idx` (0-indexed) of the sequence modulo \(10^9 + 7\).  
If the index is greater than or equal to the length of the sequence, return `-1`.

---

## Example

Input  
["Fancy","append","addAll","append","multAll","getIndex","addAll","append","multAll","getIndex","getIndex","getIndex"]

[[],[2],[3],[7],[2],[0],[3],[10],[2],[0],[1],[2]]

Output  
[null,null,null,null,null,10,null,null,null,26,34,20]

Explanation  

Fancy fancy = new Fancy()

append(2) → [2]  
addAll(3) → [5]  
append(7) → [5,7]  
multAll(2) → [10,14]  
getIndex(0) → 10  

addAll(3) → [13,17]  
append(10) → [13,17,10]  
multAll(2) → [26,34,20]  

getIndex(0) → 26  
getIndex(1) → 34  
getIndex(2) → 20  

---

## Constraints

- `1 <= val, inc, m <= 100`
- `0 <= idx <= 10^5`
- At most `10^5` calls will be made to append, addAll, multAll, and getIndex.

---

## Solution

```python
class Fancy:
    def __init__(self):
        self.mod = 10**9 + 7
        self.val = []
        self.a = 1
        self.b = 0

    def append(self, val):
        x = (val - self.b + self.mod) % self.mod
        self.val.append(x * pow(self.a, self.mod - 2, self.mod) % self.mod)

    def addAll(self, inc):
        self.b = (self.b + inc) % self.mod

    def multAll(self, m):
        self.a = (self.a * m) % self.mod
        self.b = (self.b * m) % self.mod

    def getIndex(self, idx):
        if idx >= len(self.val):
            return -1
        return (self.a * self.val[idx] + self.b) % self.mod