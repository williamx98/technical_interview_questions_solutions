# Island Perimeter  

[Question Link](https://leetcode.com/problems/island-perimeter/)  

You are given a map in form of a two-dimensional integer grid where 1 represents land and 0 represents water.  

Grid cells are connected horizontally/vertically (not diagonally). The grid is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells).  

The island doesn't have "lakes" (water inside that isn't connected to the water around the island). One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.  

### Explanation:
TLDR: On every array value of 1, add four to the total perimeter. Then, inspect the surrounding 4 locations, up, down, left and right, and subtract 1 if those values are 1. 


## Solution:
```Python
class Solution(object):
    def islandPerimeter(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        total = 0
        for row in range(len(grid)):
            for col in range(len(grid[row])):
                if grid[row][col] == 1:
                    total += 4
                    
                    if row - 1 >= 0 and grid[row - 1][col] == 1:
                        total -= 1
                        
                    if row + 1 < len(grid) and grid[row + 1][col] == 1:
                        total -= 1
                        
                    if col - 1 >= 0 and grid[row][col - 1] == 1:
                        total -= 1
                        
                    if col + 1 < len(grid[row]) and grid[row][col + 1] == 1:
                        total -= 1
                    
        return total
```