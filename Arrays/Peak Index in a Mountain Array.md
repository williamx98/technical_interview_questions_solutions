# Peak Index in a Mountain Array

[Question Link](https://leetcode.com/problems/peak-index-in-a-mountain-array/)  

Let's call an array A a mountain if the following properties hold:  

A.length >= 3  
There exists some 0 < i < A.length - 1 such that A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1]  
Given an array that is definitely a mountain, return any i such that A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1].  

### Explanation:
TLDR: Super complicated way to say return the index of the max value

## Solution:
```Python
class Solution(object):
    def peakIndexInMountainArray(self, A):
        """
        :type A: List[int]
        :rtype: int
        """
        max = A[0]
        maxIndex = 0
        
        for i,a in enumerate(A):
            if a > max:
                max = a
                maxIndex = i
                
        return maxIndex
```
