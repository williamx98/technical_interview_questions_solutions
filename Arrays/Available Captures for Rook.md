# Available Captures for Rook  
### Rating: [2/5] Good intro into matrix traversal. Somewhat convoluted.

[Question Link](https://leetcode.com/problems/available-captures-for-rook/)  

On an 8 x 8 chessboard, there is one white rook.  There also may be empty squares, white bishops, and black pawns.  These are given as characters 'R', '.', 'B', and 'p' respectively. Uppercase characters represent white pieces, and lowercase characters represent black pieces.  

The rook moves as in the rules of Chess: it chooses one of four cardinal directions (north, east, west, and south), then moves in that direction until it chooses to stop, reaches the edge of the board, or captures an opposite colored pawn by moving to the same square it occupies.  Also, rooks cannot move into the same square as other friendly bishops.  

Return the number of pawns the rook can capture in one move.  

### Explanation:
TLDR: Traversal in the possible directions until either a piece (of any type is found) or the end of the board is reached.  Add one if you ran into an opposing piece.  

The question is a little confusing even if you already know the rules of chess.

The answer you need to return is, "how many pawns are vulnerable to the rook in the board's given state?"

If there is a pawn behind another pawn (either row-wise or column-wise), the rook will not be able to capture the further pawn in one move. The rook would have to first capture the closer-pawn and then capture the previously further pawn. This would take two moves.

## Solution:
```Python
class Solution:
    def numRookCaptures(self, board):
        # find the rook
        rookX = 0
        rookY = 0
        rLen = len(board)
        cLen = len(board[0])
        for i in range(rLen):
            for j in range(cLen):
                if board[i][j] == 'R':
                    rookX = i
                    rookY = j
                    break
    
        # method to count pieces rook can take out
        def check(checkX, checkY, direction):
            while checkX > 0 and checkX < rLen - 1 and checkY > 0 and checkY < cLen - 1:
                checkX += direction[0]
                checkY += direction[1]
                
                if board[checkX][checkY] == 'B':
                    return 0
                
                if board[x][checkY] == 'p':
                    return 1
            return 0
        
        # count all the pieces that the rook for ALL directions
        count = 0
        for direction in [[1,0],[-1,0],[0,1],[0,-1]]:
            count += check(rookX, rookY, direction)
        
        return count
```
