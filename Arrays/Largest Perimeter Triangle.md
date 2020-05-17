# Largest Perimeter Triangle  

## Rating: [5/5] Good question. Somewhat complicated solution.

[Question Link](https://leetcode.com/problems/largest-perimeter-triangle/)  

Given an array A of positive lengths, return the largest perimeter of a triangle with non-zero area, formed from 3 of these lengths.  

If it is impossible to form any triangle of non-zero area, return 0.  

### Explanation:
TLDR: Sort the edges, chose the 3 consecutive sides that can form a triangle.

Why the largest consecutive 3 sides?
* 3 sides cannot form a triangle when the longest side is too long i.e the other two sides cannot connect to themselves and the ends of the longest side.  
  - We are "eliminating" the largest possible side by shifting the window every time we can't find a valid triplet.
    - We don't ever eliminate the 2nd largest possible side or 3 largest possible side
    - the answer is guaranteed to be consecutive

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
