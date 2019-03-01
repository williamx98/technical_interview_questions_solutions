# Sort Array By Parity

[Question Link](https://leetcode.com/problems/sort-array-by-parity/)  

Given an array A of non-negative integers, return an array consisting of all the even elements of A, followed by all the odd elements of A.  

You may return any answer array that satisfies this condition.  

##### Constraints:

### Explanation:
TLDR: use pointers to swap nodes when BOTH the counters point to 2 out of place items.

### Notes:
i points to the index of the array to set to the even value at j


## Solution:
```Python
class Solution(object):
    def sortArrayByParity(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        i = 0
        for j in xrange(len(A)):
            if A[j] % 2 == 0:
                temp = A[i]
                A[i] = A[j]
                A[j] = temp

                i += 1
        return A
```

```Python
class Solution(object):
    def sortArrayByParity(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        index = 0
        swapSize = 0
        
        while index + swapSize < len(A):
            if A[index + swapSize] % 2 == 1:
                swapSize += 1
            else:
                temp = A[index + swapSize]
                A[index + swapSize] = A[index]
                A[index] = temp
                index += 1
        
        return A
```
