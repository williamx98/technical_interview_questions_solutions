# 4Sum II  

[Question Link](https://leetcode.com/problems/4sum-ii/)  

Given four lists A, B, C, D of integer values, compute how many tuples (i, j, k, l) there are such that A[i] + B[j] + C[k] + D[l] is zero.  

To make problem a bit easier, all A, B, C, D have same length of N where 0 ≤ N ≤ 500. All integers are in the range of -228 to 228 - 1 and the result is guaranteed to be at most 231 - 1.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def fourSumCount(self, A, B, C, D):
        """
        :type A: List[int]
        :type B: List[int]
        :type C: List[int]
        :type D: List[int]
        :rtype: int
        """
        cache = {}
        for a in A:
            for b in B:
                total = a + b
                if total not in cache:
                    cache[total] = 0
                cache[total] += 1
                
        answer = 0
        for c in C:
            for d in D:
                total = c + d
                target = -total
                if target in cache:
                    answer += cache[target]
                
        return answer
```