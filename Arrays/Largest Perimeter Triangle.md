# Largest Perimeter Triangle  

[Question Link](https://leetcode.com/problems/largest-perimeter-triangle/)  

Given an array A of positive lengths, return the largest perimeter of a triangle with non-zero area, formed from 3 of these lengths.  

If it is impossible to form any triangle of non-zero area, return 0.  

### Explanation:
TLDR: Sort the edges, chose the largest three that can form a triangle.

## Solution:
```Python
        A.sort(reverse = True)
        
        sorted = A
        
        for index in xrange(2, len(sorted), 1):
            first = sorted[index - 2]
            second = sorted[index - 1]
            third = sorted[index]
            
            if second + third > first:
                return second + third + first
            
        return 0
```
