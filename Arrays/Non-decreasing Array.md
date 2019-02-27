# Non-decreasing Array  

[Question Link](https://leetcode.com/problems/non-decreasing-array/)  

Given an array with n integers, your task is to check if it could become non-decreasing by modifying at most 1 element.  

We define an array is non-decreasing if array[i] <= array[i + 1] holds for every i (1 <= i < n).  

##### Constraints:

### Explanation:
TLDR: Reduce the problem to a smaller size. If there are two locations where A[i] is greater than A[i + 1], then its not possible. 

### Notes:
The brute force solution is to change A[i] to A[i + 1] if A[i] > A[i]. Then check if the array is non-decreasing. This would be an O(n^2) operation.

## Solution:
```Python
class Solution(object):
    def checkPossibility(self, A):
        p = None
        for i in xrange(len(A) - 1):
            if A[i] > A[i+1]:
                if p is not None:
                    return False
                p = i

        return (p is None or p == 0 or p == len(A)-2 or A[p-1] <= A[p+1] or A[p] <= A[p+2])
```