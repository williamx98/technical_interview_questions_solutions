# Sort Array By Parity

[Question Link](https://leetcode.com/problems/sort-array-by-parity/)  

Given an array A of non-negative integers, return an array consisting of all the even elements of A, followed by all the odd elements of A.  

You may return any answer array that satisfies this condition.  

##### Constraints:

### Explanation:
TLDR: use pointers to swap nodes when BOTH the counters point to 2 out of place items.

### Notes:


## Solution With Comments:
```Python
class Solution(object):
    def sortArrayByParity(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        if len(A) == 1:
            return A
        
        leftPointer = 0
        rightPointer = len(A) - 1
        
        while leftPointer < rightPointer:
            if A[leftPointer] % 2 == 1 and A[rightPointer] % 2 == 0:
                temp = A[leftPointer]
                A[leftPointer] = A[rightPointer]
                A[rightPointer] = temp
                
            if A[leftPointer] % 2 == 0:
                leftPointer += 1
            
            if A[rightPointer] % 2 == 1:
                rightPointer -= 1
                
        return A
```


## Solution Without Comments:
```Python

```