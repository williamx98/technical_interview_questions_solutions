# Max Increase to Keep City Skyline  

[Question Link](https://leetcode.com/problems/max-increase-to-keep-city-skyline/)  

In a 2 dimensional array grid, each value grid[i][j] represents the height of a building located there. We are allowed to increase the height of any number of buildings, by any amount (the amounts can be different for different buildings). Height 0 is considered to be a building as well.  

At the end, the "skyline" when viewed from all four directions of the grid, i.e. top, bottom, left, and right, must be the same as the skyline of the original grid. A city's skyline is the outer contour of the rectangles formed by all the buildings when viewed from a distance. See the following example.  

What is the maximum total sum that the height of the buildings can be increased?  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def maxIncreaseKeepingSkyline(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        total = 0
        
        hor = []
        ver = []
        
        for row in range(len(grid)):
            max = 0
            for col in range(len(grid[row])):
                total -= grid[row][col]
                if grid[row][col] > max:
                    max = grid[row][col]
            hor.append(max)
        
        for col in range(len(grid[0])):
            max = 0
            for row in range(len(grid)):
                if grid[row][col] > max:
                    max = grid[row][col]
            ver.append(max)
        
        for h in hor:
            for v in ver:
                total += min(h, v)
                
        return total
                
```		