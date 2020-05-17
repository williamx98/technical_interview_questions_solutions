# Monotonic Array  

### Rating: [5/5] Good intro into array traversal. Super straight forward solution.

[Question Link](https://leetcode.com/problems/monotonic-array/)  

An array is monotonic if it is either monotone increasing or monotone decreasing.  

An array A is monotone increasing if for all i <= j, A[i] <= A[j].  An array A is monotone decreasing if for all i <= j, A[i] >= A[j].  

Return true if and only if the given array A is monotonic.  

### Explanation:
TLDR: Assume that the array is both always increasing and always decreasing. Only one will can be true upon checking. 

## Solution:
```Python
class Solution(object):
    def isMonotonic(self, A):
        """
        :type A: List[int]
        :rtype: bool
        """
        if len(A) <= 2:
            return True
        
        inc = True
        dcr = True
        
        for index in xrange(1, len(A)):
            cur = A[index - 1]
            nxt = A[index]
            
            if cur > nxt:
                inc = False
            elif cur < nxt:
                dcr = False
            
            # optimization: quit when you know neither are true
            if inc == False and dcr == False:
                return False
        
        return inc or dcr
```
