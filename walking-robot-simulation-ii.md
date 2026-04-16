# Walking Robot Simulation II

## Problem

A `width x height` grid is on an XY-plane with the bottom-left cell at `(0, 0)` and the top-right cell at `(width - 1, height - 1)`.

The robot starts at position `(0, 0)` facing **East**.

For every step:

1. The robot tries to move forward one cell in its current direction.
2. If the next cell is **out of bounds**, the robot turns **90° counterclockwise** and retries the step.

Implement the `Robot` class.

### Methods

**Robot(width, height)**  
Initializes the robot at `(0,0)` facing `"East"`.

**step(num)**  
Moves the robot `num` steps following the rules.

**getPos()**  
Returns the robot’s current position `[x, y]`.

**getDir()**  
Returns the robot’s current direction (`"North"`, `"East"`, `"South"`, `"West"`).

---

## Example

Input  

["Robot","step","step","getPos","getDir","step","step","step","getPos","getDir"]

[[6,3],[2],[2],[],[],[2],[1],[4],[],[]]

Output  

[null,null,null,[4,0],"East",null,null,null,[1,2],"West"]

Explanation  

Robot robot = new Robot(6,3)

step(2) → (2,0) East  
step(2) → (4,0) East  

getPos() → [4,0]  
getDir() → "East"

step(2) → (5,1) North  
step(1) → (5,2) North  
step(4) → (1,2) West  

getPos() → [1,2]  
getDir() → "West"

---

## Constraints

- `2 <= width, height <= 100`
- `1 <= num <= 10^5`
- At most `10^4` calls to step/getPos/getDir

---

## Solution

```python
class Robot:

    def __init__(self, width, height):
        self.x = 0
        self.y = 0
        self.dir = "East"
        self.width = width
        self.height = height

    def step(self, num):
        perimeter = 2 * (self.width - 1) + 2 * (self.height - 1)

        num %= perimeter
        if num == 0:
            num = perimeter

        while num > 0:
            nx, ny = self.x, self.y

            if self.dir == "East":
                maxX = min(self.x + num, self.width - 1)
                rem = num - (maxX - self.x)
                num = rem

                if rem == 0:
                    self.x, self.y = maxX, ny
                else:
                    self.x = maxX
                    self.dir = "North"

            elif self.dir == "West":
                minX = max(self.x - num, 0)
                rem = num - (self.x - minX)
                num = rem

                if rem == 0:
                    self.x, self.y = minX, ny
                else:
                    self.x = minX
                    self.dir = "South"

            elif self.dir == "North":
                maxY = min(self.y + num, self.height - 1)
                rem = num - (maxY - self.y)
                num = rem

                if rem == 0:
                    self.x, self.y = nx, maxY
                else:
                    self.y = maxY
                    self.dir = "West"

            elif self.dir == "South":
                minY = max(self.y - num, 0)
                rem = num - (self.y - minY)
                num = rem

                if rem == 0:
                    self.x, self.y = nx, minY
                else:
                    self.y = minY
                    self.dir = "East"

    def getPos(self):
        return [self.x, self.y]

    def getDir(self):
        return self.dir