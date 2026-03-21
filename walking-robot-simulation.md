# Walking Robot Simulation

## Problem

A robot on an infinite XY-plane starts at point (0, 0) facing north. The robot receives an array of integers `commands` representing instructions.

Instructions can be:

- `-2`: Turn left 90 degrees
- `-1`: Turn right 90 degrees
- `1 <= k <= 9`: Move forward `k` units

Some grid squares contain obstacles. If the robot encounters an obstacle, it stops before the obstacle and continues with the next command.

Return the **maximum squared Euclidean distance from the origin** that the robot reaches during its path.

### Directions

- North → +Y  
- East → +X  
- South → -Y  
- West → -X  

### Example 1

Input  
commands = [4,-1,3]  
obstacles = []

Output  
25

Explanation  
The robot moves to (3,4). Distance² = 3² + 4² = 25.

### Example 2

Input  
commands = [4,-1,4,-2,4]  
obstacles = [[2,4]]

Output  
65

### Example 3

Input  
commands = [6,-1,-1,6]  
obstacles = [[0,0]]

Output  
36

### Constraints

- `1 <= commands.length <= 10^4`
- `commands[i] ∈ {-2, -1} ∪ [1,9]`
- `0 <= obstacles.length <= 10^4`
- `-3 * 10^4 <= xi, yi <= 3 * 10^4`

## Solution

```python
class Solution(object):
    def robotSim(self, commands, obstacles):
        obstacle_set = set(map(tuple, obstacles))
        x, y = 0, 0
        direction = 0
        dx = [0, 1, 0, -1]
        dy = [1, 0, -1, 0]
        max_dist = 0
        for cmd in commands:
            if cmd == -1:
                direction = (direction + 1) % 
            elif cmd == -2:
                direction = (direction + 3) % 4
            else:
                for _ in range(cmd):
                    nx = x + dx[direction]
                    ny = y + dy[direction]
                    if (nx, ny) in obstacle_set:
                        break
                    x, y = nx, ny
                    max_dist = max(max_dist, x*x + y*y)

        return max_dist