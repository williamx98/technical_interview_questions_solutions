# Self Dividing Numbers

[Question Link](https://leetcode.com/problems/self-dividing-numbers/)  

A self-dividing number is a number that is divisible by every digit it contains.  

For example, 128 is a self-dividing number because 128 % 1 == 0, 128 % 2 == 0, and 128 % 8 == 0.  

Also, a self-dividing number is not allowed to contain the digit zero.  

Given a lower and upper number bound, output a list of every possible self dividing number, including the bounds if possible.  

##### Constraints:

### Explanation:
TLDR:

### Notes:


## Solution:
```Python
class Solution(object):
    def selfDividingNumbers(self, left, right):
        """
        :type left: int
        :type right: int
        :rtype: List[int]
        """
        
        def selfDividing(val):
            base = val
            while base > 0:
                digit = base % 10
                if digit == 0 or val % digit != 0:
                    return False
                base = base / 10
                
            return True
        
        answer = [];
        for val in xrange(left, right + 1):
            if selfDividing(val):
                answer.append(val)
                
        return answer
```