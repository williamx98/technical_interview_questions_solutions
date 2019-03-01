# Sort Array By Parity II

[Question Link](https://leetcode.com/problems/sort-array-by-parity-ii/)  
Given an array A of non-negative integers, half of the integers in A are odd, and half of the integers are even.  

Sort the array so that whenever A[i] is odd, i is odd; and whenever A[i] is even, i is even.  

You may return any answer array that satisfies this condition.  

### Explanation:
TLDR: Swap when the pointers point to indexes when I doesn't meet its criteria. Move pointers when they are in the right place.

## Solution:
```Python
class Solution(object):
    def sortArrayByParityII(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        even = 0
        odd = 1
        
        while even < len(A) and odd < len(A):
            if A[even] % 2 == 1 and A[odd] % 2 == 0:
                temp = A[even]
                A[even] = A[odd]
                A[odd] = temp
            
            if A[even] % 2 == 0:
                even = even + 2
                
            if A[odd] % 2 == 1:
                odd = odd + 2
                
        return A
```
