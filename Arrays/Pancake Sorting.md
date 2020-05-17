# Pancake Sorting  

### Rating: [3/5] Convoluted Question. Not impossible but convoluted solution. Hard to infer. 

[Question Link](https://leetcode.com/problems/pancake-sorting/)  

Given an array A, we can perform a pancake flip: We choose some positive integer k <= A.length, then reverse the order of the first k elements of A.  We want to perform zero or more pancake flips (doing them one after another in succession) to sort the array A.  

Return the k-values corresponding to a sequence of pancake flips that sort A.  Any valid answer that sorts the array within 10 * A.length flips will be judged as correct.  

### Explanation:
Sort by largest to smallest.
Find the largest unsorted element i.e find the largest element that is not in the right place.
Then, reverse the values from index 0 up to and including the unsorted value.
Then, reverse all the values from index 0 to where the unsorted value belongs.
Repeat with the next largest unsorted value.

## Solution:
```Python
class Solution(object):
    def pancakeSort(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        # straight forward reversing function
        def reverse(arr, k):
            i = 0
            j = k
            while i < j:
                tmp = arr[i]
                arr[i] = arr[j]
                arr[j] = tmp
                
                i += 1
                j -= 1
    
        answer = []
        for targetValue in xrange(len(A), 0, -1):
            # find the targetValue in the array

            searchIndex = targetValue - 1
            while A[searchIndex] != targetValue:
                searchIndex -= 1

            if searchIndex + 1 != targetValue:
                answer.append(searchIndex + 1)
                reverse(A, searchIndex)
                
                answer.append(targetValue)
                reverse(A, targetValue - 1)
        return answer
```
