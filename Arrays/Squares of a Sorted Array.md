# Squares of a Sorted Array

[Question Link](https://leetcode.com/problems/squares-of-a-sorted-array/)  

Given an array of integers A sorted in non-decreasing order, return an array of the squares of each number, also in sorted non-decreasing order.

### Explanation:
TLDR: Compare a moving front pointer to a moving back pointer and add the greater to the end of the answer array and move that pointer torwards the center.

## Solution:
```Python
class Solution(object):
    def sortedSquares(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        
        AFront = 0
        AEnd = len(A) - 1
        answerEnd = AEnd
        answerArray = [0] * (AEnd + 1)
        
        while AFront <= AEnd:
            frontCompare = A[AFront] * A[AFront]
            endCompare = A[AEnd] * A[AEnd]
            
            if frontCompare >= endCompare:
                answerArray[answerEnd] = frontCompare
                AFront = AFront + 1
            else:
                answerArray[answerEnd] = endCompare
                AEnd = AEnd - 1
                
            answerEnd = answerEnd - 1

        return answerArray
```
