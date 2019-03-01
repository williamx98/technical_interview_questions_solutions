# N-Repeated Element in Size 2N Array

[Question Link](https://leetcode.com/problems/n-repeated-element-in-size-2n-array/)  

In a array A of size 2N, there are N+1 unique elements, and exactly one of these elements is repeated N times.  

Return the element repeated N times.

### Explanation:
TLDR: Only one duplicated element  

There is only one duplicated element so keep track of the seen elements in a set for speedy checking

## Solution:
```Python
class Solution(object):
    def repeatedNTimes(self, A):
        """
        :type A: List[int]
        :rtype: int
        """
        seen = set()
        for a in A:
            if a in seen:
                return a
            else:
                seen.add(a)
```
