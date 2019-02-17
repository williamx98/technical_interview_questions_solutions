# DI String Match

[Question Link](https://leetcode.com/problems/di-string-match/)  

Given a string S that only contains "I" (increase) or "D" (decrease), let N = S.length.  

Return any permutation A of [0, 1, ..., N] such that for all i = 0, ..., N-1:  

If S[i] == "I", then A[i] < A[i+1]  
If S[i] == "D", then A[i] > A[i+1]  


##### Constraints:

### Explanation:
TLDR: I starts at 0, D starts at the length of S. Set to I when "I", set to D when "D", increment on I, decrement on D. Add I or D on end.

### Notes:
Remember to add I or D on the end.


## Solution:
```Python
class Solution(object):
    def diStringMatch(self, S):
        """
        :type S: str
        :rtype: List[int]
        """
        I = 0
        D = len(S)
        
        answer = [0] * (len(S) + 1)
        
        
        for i,s in enumerate(S):
            if s == "I":
                answer[i] = I
                I = I + 1
            elif s == "D":
                answer[i] = D
                D = D - 1
                
        answer[-1] = D
        
        return answer
```