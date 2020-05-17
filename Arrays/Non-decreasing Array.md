# Non-decreasing Array  

### Rating: [4/5] Good question. Somewhat complicated answer, hard to infer.

[Question Link](https://leetcode.com/problems/non-decreasing-array/)  

Given an array with n integers, your task is to check if it could become non-decreasing by modifying at most 1 element.  

We define an array is non-decreasing if array[i] <= array[i + 1] holds for every i (1 <= i < n).  

### Explanation:
TLDR: Reduce the problem to a smaller size. If there are two locations where A[i] is greater than A[i + 1], then its not possible. 

### Notes:
The brute force solution is to change A[i] to A[i + 1] if A[i] > A[i]. Then check if the array is non-decreasing. This would be an O(n^2) operation.

## Solution:
```Python
class Solution(object):
    def checkPossibility(self, A):
        indexOfDecrease = None
        for currentIndex in xrange(len(A) - 1):
            if A[currentIndex] > A[currentIndex+1]:
                if indexOfDecrease is not None:
                    return False
                indexOfDecrease = currentIndex

        return (indexOfDecrease is None or # no decreases
        		indexOfDecrease == 0 or # decrease between 0 - 1, make 0 lower than 1
        		indexOfDecrease == len(A)-2 or # decrease happens before the last element. Make the last element larger than the previous element.
        		A[indexOfDecrease - 1] <= A[indexOfDecrease + 1] or # in [...a, b, c], decrease happens between b and c. When a <= c, make b = c.
        		A[indexOfDecrease] <= A[indexOfDecrease + 2]) # in [... a, b, c], decrease happens between a and b. When a <= c, make b = c
```
