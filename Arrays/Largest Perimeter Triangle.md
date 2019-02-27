# Largest Perimeter Triangle  

[Question Link](https://leetcode.com/problems/largest-perimeter-triangle/)  

Given an array A of positive lengths, return the largest perimeter of a triangle with non-zero area, formed from 3 of these lengths.  

If it is impossible to form any triangle of non-zero area, return 0.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
#         def sort(array):
#             if len(array) <= 1:
#                 return array
            
#             mid = len(array)//2
        
#             sortedLeft = sort(array[0:mid])
#             sortedRight = sort(array[mid:len(array)])
            
#             mergedSorted = []
                
#             l = 0
#             r = 0
            
#             leftLength = len(sortedLeft)
#             rightLength = len(sortedRight)
            
#             while l < leftLength or r < rightLength:
#                 valueToAppend = None
#                 if l < leftLength and (r >= rightLength or sortedLeft[l] >= sortedRight[r]):
#                     valueToAppend = sortedLeft[l]
#                     l = l + 1
#                 else:
#                     valueToAppend = sortedRight[r]
#                     r = r + 1
                    
#                 mergedSorted.append(valueToAppend)
            
#             return mergedSorted
        
#         sorted = sort(A)
        
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