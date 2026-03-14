# Robot Return to Origin

## Problem

There is a robot starting at the position (0, 0), the origin, on a 2D plane. Given a sequence of its moves, judge if the robot ends up at (0, 0) after completing all moves.

You are given a string moves where each character represents a move:
'U' (up), 'D' (down), 'L' (left), and 'R' (right).

Return true if the robot returns to the origin after finishing all moves, otherwise return false.

Example 1

Input: moves = "UD"  
Output: true  

Explanation  
The robot moves up once and down once, returning to the origin.

Example 2

Input: moves = "LL"  
Output: false  

Explanation  
The robot moves left twice and does not return to the origin.

Constraints

1 <= moves.length <= 2 * 10^4  
moves only contains 'U', 'D', 'L', and 'R'

## Solution

```python
class Solution(object):
    def judgeCircle(self, moves):
        x, y = 0, 0
        for move in moves:
            if move == 'U':
                y += 1
            elif move == 'D':
                y -= 1
            elif move == 'R':
                x += 1
            elif move == 'L':
                x -= 1

        return x == 0 and y == 0