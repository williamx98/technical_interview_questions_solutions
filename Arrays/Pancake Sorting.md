# Pancake Sorting  

[Question Link](https://leetcode.com/problems/pancake-sorting/submissions/)  

Given an array A, we can perform a pancake flip: We choose some positive integer k <= A.length, then reverse the order of the first k elements of A.  We want to perform zero or more pancake flips (doing them one after another in succession) to sort the array A.  

Return the k-values corresponding to a sequence of pancake flips that sort A.  Any valid answer that sorts the array within 10 * A.length flips will be judged as correct.  

##### Constraints:

### Explanation:
TLDR: Find the max, flip the values up to and including max, then flip the max to its position by flipping k = max value. then repeat with max - 1.

### Notes:


## Solution:
```Python
class Solution(object):
    def pancakeSort(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        def reverse(arr, k):
            i = 0
            j = k - 1
            while i < j:
                tmp = arr[i]
                arr[i] = arr[j]
                arr[j] = tmp
                
                i += 1
                j -= 1
    
        res = []
        for index in xrange(len(A), 0, -1):
            k = 0
            while A[k] != index:
                k += 1
                
            reverse(A, k + 1)
            res.append(k + 1)
            reverse(A, index)
            res.append(index)
            
        return res
```