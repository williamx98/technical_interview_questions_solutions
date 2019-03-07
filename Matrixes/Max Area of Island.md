# Max Area of Island  

[Question Link](https://leetcode.com/problems/max-area-of-island/)  

Given a non-empty 2D array grid of 0's and 1's, an island is a group of 1's (representing land) connected 4-directionally (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.  

Find the maximum area of an island in the given 2D array. (If there is no island, the maximum area is 0.)  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


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
                
                connected = 0
                toVisit = [(r,c)]
                grid[r][c] = 0
                
                while toVisit:
                    currR, currC = toVisit.pop()
                    connected += 1
                    
                    for tryR, tryC in [(currR - 1, currC), (currR + 1, currC), (currR, currC - 1), (currR, currC + 1)]:
                        if tryR < 0 or tryR >= rowLen:
                            continue
                            
                        if tryC < 0 or tryC >= colLen:
                            continue
                            
                        if grid[tryR][tryC] == 1:
                            grid[tryR][tryC] = 0
                            toVisit.append((tryR, tryC))
                            
                    ans = max(ans, connected)
                
        return ans
```