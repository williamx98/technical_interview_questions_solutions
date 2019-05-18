# Generate Parentheses  

[Question Link](https://leetcode.com/problems/generate-parentheses/)  

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.  

### Explanation:
TLDR: 

## Solution:
```Python
class Solution(object):
    def generateParenthesis(self, N):
        ans = []
        
        def backtrack(S, open, close):
            if len(S) == 2 * N:
                ans.append(S)
                return
            
            if open < N:
                backtrack(S + '(', open + 1, close)
                
            if close < open:
                backtrack(S + ')', open, close + 1)

        backtrack('', 0, 0)
        return ans
```