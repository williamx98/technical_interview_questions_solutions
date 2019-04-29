# Remove Outermost Parentheses  

[Question Link](https://leetcode.com/problems/remove-outermost-parentheses/)  

*This is another one of Leetcodes convoluted questions.*  
*The main takeaway is paraenthesis/bracket balancing*  

A valid parentheses string is either empty (""), "(" + A + ")", or A + B, where A and B are valid parentheses strings, and + represents string concatenation.  For example, "", "()", "(())()", and "(()(()))" are all valid parentheses strings.

A valid parentheses string S is primitive if it is nonempty, and there does not exist a way to split it into S = A+B, with A and B nonempty valid parentheses strings.

Given a valid parentheses string S, consider its primitive decomposition: S = P_1 + P_2 + ... + P_k, where P_i are primitive valid parentheses strings.

Return S after removing the outermost parentheses of every primitive string in the primitive decomposition of S.


### Explanation:
TLDR: 

## Solution:
```Python
class Solution(object):
    def removeOuterParentheses(self, S):
        
        open = 0
        ans  = ''
        cnt = 0
        
        for idx, ch in enumerate(S):
            if ch == '(':
                cnt += 1
            elif ch == ')':
                cnt -= 1

            if cnt == 0:
                ans += S[open+1:idx]
                open = idx+1
                
        return ans
```