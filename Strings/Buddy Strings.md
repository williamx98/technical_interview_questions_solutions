# Buddy Strings  

[Question Link](https://leetcode.com/problems/buddy-strings/)  

Given two strings A and B of lowercase letters, return true if and only if we can swap two letters in A so that the result equals B.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def buddyStrings(self, A, B):
        """
        :type A: str
        :type B: str
        :rtype: bool
        """
        
        if len(A) != len(B) or len(A) < 2 or len(B) < 2:
            return False

        if A == B:
            return len(A) != len(set(A))
        
        A = list(A)
        B = list(B)
        
        indexes = []
        
        for index in xrange(len(A)):
            if len(indexes) > 2:
                return False
            
            if A[index] != B[index]:
                indexes.append(index)

        if len(indexes) != 2:
            return False
                
        temp = A[indexes[0]]
        A[indexes[0]] = A[indexes[1]]
        A[indexes[1]] = temp
        
        return A == B
```