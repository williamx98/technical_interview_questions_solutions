# Max Area of Island  

### Rating: [5/5] Good intro into BFS. Nothing special but most straight forward application of BFS.

[Question Link](https://leetcode.com/problems/max-area-of-island/)  

Given a non-empty 2D array grid of 0's and 1's, an island is a group of 1's (representing land) connected 4-directionally (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.  

Find the maximum area of an island in the given 2D array. (If there is no island, the maximum area is 0.)  

### Explanation:
TLDR: Using basic BFS to find connected components

## Solution:
```Python
class Solution(object):
    def maxAreaOfIsland(self, grid):
        ans = 0
        
        rowLen = len(grid)
        colLen = len(grid[0])
        
        for r, row in enumerate(grid):
            for c, val in enumerate(row):
                if val == 0:
                    continue
                
                sizeOfCurrentIsland = 0
                coordinatesToVisit = [(r,c)]
                # mark current coordinate as visited
                grid[r][c] = 0
                
                while coordinatesToVisit:
                    visitingX, visitingY = coordinatesToVisit.pop()
                    sizeOfCurrentIsland += 1
                    
                    for dX, dY in [(-1, 0), (1, 0), (0, -1), (0, 1)]:
                        
                        surroundingX = visitingX + dX
                        surroundingY = visitingY + dY

                        if surroundingX < 0 or surroundingX >= rowLen:
                            continue
                            
                        if surroundingY < 0 or surroundingY >= colLen:
                            continue
                            
                        if grid[surroundingX][surroundingY] == 1:
                            grid[surroundingX][surroundingY] = 0
                            coordinatesToVisit.append((surroundingX, surroundingY))
                            
                    ans = max(ans, sizeOfCurrentIsland)
                
        return ans
```
