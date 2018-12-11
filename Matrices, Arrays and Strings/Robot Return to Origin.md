# Robot Return to Origin

[Question Link](https://leetcode.com/problems/robot-return-to-origin/)  

There is a robot starting at position (0, 0), the origin, on a 2D plane. Given a sequence of its moves, judge if this robot ends up at (0, 0) after it completes its moves.  

The move sequence is represented by a string, and the character moves[i] represents its ith move. Valid moves are R (right), L (left), U (up), and D (down). If the robot returns to the origin after it finishes all of its moves, return true. Otherwise, return false.  

Note: The way that the robot is "facing" is irrelevant. "R" will always make the robot move to the right once, "L" will always make it move left, etc. Also, assume that the magnitude of the robot's movement is the same for each move.  

##### Constraints:

### Explanation:
TLDR: All we care about is the over direction change which can be tracked with two variables defining the axis we can move in.

### Notes:


## Solution With Comments:
```Python
class Solution(object):
    def judgeCircle(self, moves):
        """
        :type moves: str
        :rtype: bool
        """
        ver = 0
        hor = 0
        
        for move in moves:
            if move == 'U':
                ver += 1
                continue

            if move == 'D':
                ver -= 1
                continue

            if move == 'L':
                hor -= 1
                continue

            if move == 'R':
                hor += 1
                continue

                
        return ver == 0 and hor == 0
```