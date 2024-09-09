<!-- Setp-4 -->

# LeetCode - [874. Walking Robot Simulation](https://leetcode.com/problems/walking-robot-simulation/description/)

**Difficulty:** Medium

**Category:** Arrays, Simulation

---

## Solution

```java
class Solution {
    public int robotSim(int[] commands, int[][] obstacles) {
        int[][] directions = { { 0, 1 }, { 1, 0 }, { 0, -1 }, { -1, 0 } };
        // N , E , S , W

        int dir = 0; // Start with n

        int x = 0;
        int y = 0;
        int maxDistance = 0;

        Set<String> setObstacles = new HashSet<>();
        for (int[] row : obstacles) {
            setObstacles.add(row[0] + " " + row[1]);
        }

        for (int command : commands) {
            if (command == -1) {
                dir = (dir + 1) % 4;
            } else if (command == -2) {
                dir = (dir + 3) % 4;
            } else {
                for (int i = 1; i <= command; i++) {
                    int newX = x + directions[dir][0];
                    int newY = y + directions[dir][1];

                    if (setObstacles.contains(newX + " " + newY)) {
                        break;
                    }
                    x = newX;
                    y = newY;
                }

                maxDistance = Math.max(maxDistance, (x * x + y * y));
            }
        }

        return maxDistance;
    }
}
```
