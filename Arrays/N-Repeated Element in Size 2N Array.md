# N-Repeated Element in Size 2N Array

### Rating: [4/5] Good intro into array traversal and sets. Straight forward answer. Good advanced solution.

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

## Advanced Solution:
```Python
class Solution(object):
    def repeatedNTimes(self, A):
        for subarrayStartingIndex in xrange(len(A) - 3):
            seen = set()
            for index in xrange(subarrayStartingIndex, subarrayStartingIndex + 4):
                if A[index] in seen:
                    return A[index];
                else:
                    seen.add(A[index])
```
## Advanced Solution:
```Python
class Solution(object):
    def repeatedNTimes(self, A):
        for subarrayIndexDelta in xrange(1, 4):
            for subarrayStartingIndex in xrange(len(A) - subarrayIndexDelta):
                if A[subarrayStartingIndex] == A[subarrayStartingIndex + subarrayIndexDelta]:
                    return A[subarrayStartingIndex]
```
