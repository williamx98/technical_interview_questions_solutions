# Projection Area of 3D Shapes

[Question Link](https://leetcode.com/problems/projection-area-of-3d-shapes/)  

On a N * N grid, we place some 1 * 1 * 1 cubes that are axis-aligned with the x, y, and z axes.  

Each value v = grid[i][j] represents a tower of v cubes placed on top of grid cell (i, j).  

Now we view the projection of these cubes onto the xy, yz, and zx planes.  

A projection is like a shadow, that maps our 3 dimensional figure to a 2 dimensional plane.  

Here, we are viewing the "shadow" when looking at the cubes from the top, the front, and the side.  

Return the total area of all three projections.  

##### Constraints:

### Explanation:
TLDR: analyze the matrix on single-item, row, then column basis.

### Notes:


## Solution:
```Python
class Solution(object):
    def projectionArea(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        total = 0
        
        for row in grid:
            max = 0
            for item in row:
                if item > 0:
                    total += 1
                    if item > max:
                        max = item    
            total += max
        
        for colIn in xrange(len(grid)):
            max = 0
            for row in grid:
                if row[colIn] > max:
                    max = row[colIn]
            total += max
            
        return total     
```