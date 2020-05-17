# Delete Columns to Make Sorted
### Rating: [0/5] Terribly worded description on LeetCode. Good for practicing matrix traversal.

[Question Link](https://leetcode.com/problems/delete-columns-to-make-sorted/)  

We are given an array A of N lowercase letter strings, all of the same length.  

Now, we may choose any set of deletion indices, and for each string, we delete all the characters in those indices.  

For example, if we have an array A = ["abcdef","uvwxyz"] and deletion indices {0, 2, 3}, then the final array after deletions is ["bef", "vyz"], and the remaining columns of A are ["b","v"], ["e","y"], and ["f","z"].  (Formally, the c-th column is [A[0][c], A[1][c], ..., A[A.length-1][c]].)  

Suppose we chose a set of deletion indices D such that after deletions, each remaining column in A is in non-decreasing sorted order.  

Return the minimum possible value of D.length.  

### Explanation:
TLDR: Find the number of columns where the it is not sorted from least to greatest columnwise

## Solution:
```Python
class Solution(object):
    def minDeletionSize(self, A):
        ans = 0
        for col in xrange(len(A[0])):
            for r in xrange(len(A) - 1):
                if A[r][col] > A[r+1][col]:
                    ans += 1
                    break;
        return ans
```
