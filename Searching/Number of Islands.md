# https://leetcode.com/explore/featured/card/queue-stack/231/practical-application-queue/1374

[Question Link](https://leetcode.com/explore/featured/card/queue-stack/231/practical-application-queue/1374)  

Given a 2d grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

##### Constraints:

### Explanation:
TLDR: A destructive DFS. Destruction can be resovled by making a copy before destroying

### Notes:

## Solution DFS:
```Python
class Solution(object):
    def numIslands(self, grid):
        """
        :type grid: List[List[str]]
        :rtype: int
        """
        def isValid(row, col, grid):
            if row < 0 or row >= len(grid):
                return False
            if col < 0 or col >= len(grid[0]):
                return False
            return grid[row][col] == '1'
        
        def DFS(row, col, grid):
            if isValid(row, col, grid) == False:
                return
            grid[row][col] = '0'
            moves = [[0,1],[1,0],[-1,0],[0,-1]]
            for move in moves:
                DFS(row+move[0], col+move[1], grid)
        
        answer = 0
        visited = set()
        for row in range(len(grid)):
            for col in range(len(grid[row])):                
                if grid[row][col] == '1':
                    DFS(row, col, grid)
                    answer += 1
                
        return answer
```