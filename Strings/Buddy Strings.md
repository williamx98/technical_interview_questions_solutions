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
        # input sorting: if the lengths of A and B are not the same, the answer is automatically false
        # if either A or B has a length less than 2 i.e 1 or 0, the answer is automatically false
        if len(A) != len(B) or len(A) < 2 or len(B) < 2:
            return False

        # if A equals B, return if there are any repeated letters
        # repeated letters can be swapped, maintaing the equivalency
        # if A does not container repeated letters, no letters can be swapped
        # those two conditions can be checked by 
        if A == B:
            return len(A) != len(set(A))
        
        # convert both strings to a list first
        A = list(A)
        # if you look at this solution, you will notice that there is never a change to B's list
        # so why is it necessary to convert B into a list?
        # To answer this, look at the very last line of the solution
        B = list(B)
        indexes = []
        
        for index in xrange(len(A)):
            # if there are more than 2 characters different, its impossible so return false
            if len(indexes) > 2:
                return False
            
            if A[index] != B[index]:
                indexes.append(index)

        if len(indexes) != 2:
            return False
                
        temp = A[indexes[0]]
        A[indexes[0]] = A[indexes[1]]
        A[indexes[1]] = temp
        
        # here we are comparing the LIST of A to the LIST B
        # that is why is necessary to convert B into a LIST
        # because this is a LIST to LIST comparision
        # an alternative would be to not make a B list and then convert the altered A list back into a string
        # i believe the amount of work is roughly the same from a high level
        return A == B
```
