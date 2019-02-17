# Spiral Matrix

[Question Link](https://leetcode.com/problems/spiral-matrix/)  

Given a matrix of m x n elements (m rows, n columns), return all elements of the matrix in spiral order.  

##### Constraints:

### Explanation:
TLDR: Bounce the "pointer" around as you travel the array

Stop traversing once the number of elements traversed == number of elements in the array.  

This solution was inspired by the game Snake, where a snake will travel indefinitely in the direction you choose with only one button press i.e press the left button once, the snake will go left forever. This solution emulates that same logic. The "head" of the snake will traverse in the given direction until it has to move in the next direction.

### Notes:


## Solution:
```Python
class Solution(object):
    def spiralOrder(self, array):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        if not array:
            return []
        
        answer = []
        togo = len(array) * len(array[0])
        row = 0
        col = 0
        up = 0
        down = len(array) - 1
        left = 0
        right = len(array[0]) - 1
        direction = [0,1]

        while togo > 0:
            answer.append(array[row][col])

            togo -= 1
            row += direction[0]
            col += direction[1]

            if col > right:
                col = right
                up += 1
                row += 1
                direction = [1,0]
            elif row > down:
                row = down
                right -= 1
                col -= 1
                direction = [0, -1]
            elif col < left:
                col = left
                down -= 1
                row -= 1
                direction = [-1, 0]
            elif row < up:
                row = up
                left += 1
                col += 1
                direction = [0,1]
        
        return answer       
```