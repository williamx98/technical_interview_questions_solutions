# Shortest Distance to a Character

[Question Link](https://leetcode.com/problems/shortest-distance-to-a-character/)  

Given a string S and a character C, return an array of integers representing the shortest distance from the character C in the string.  

Input: S = "loveleetcode", C = 'e'  
Output: [3, 2, 1, 0, 1, 0, 0, 1, 2, 2, 1, 0]

##### Constraints:

### Explanation:
TLDR: Go forward and subtract the current index from the previously found C index. Go backward and subtract the previously found C index from the current index. 

### Notes:


## Solution:
```Python
class Solution:
    def shortestToChar(self, s, C):
        """
        :type S: str
        :type C: str
        :rtype: List[int]
        """
        i = 0
        j = len(s) - 1
        front = None
        back = None
        res = [len(s)] * len(s)
        
        while i < len(s):
            if s[i] == C: 
                front = i
                
            if front != None:
                res[i] = min(res[i], i - front)
                
            i += 1
                
        while j >= 0:
            if s[j] == C:
                back = j
                
            if back != None:
                res[j] = min(res[j], -j + back)
        
            j -= 1
            
        return res            
```