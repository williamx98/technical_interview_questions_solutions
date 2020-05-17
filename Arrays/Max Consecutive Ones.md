# Max Consecutive Ones  

### Rating: [5/5] Good intro into array traversal. Super straight forward and one of the most basic applications of if/else.

[Question Link](https://leetcode.com/problems/max-consecutive-ones/)  

Given a binary array, find the maximum number of consecutive 1s in this array.  

##### Constraints:

### Explanation:
TLDR: add 1 when 1, set 0 when 0. Key step: set answer on every iteration - [0,1,1] - for when consecutive ones dont terminate with 0

## Solution:
```Python
class Solution(object):
    def findMaxConsecutiveOnes(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        count = 0
        maximum = 0
        for num in nums:
            if num == 1:
                count += 1
                maximum = max(maximum, count)
            else:
                count = 0
        
        return maximum
```
