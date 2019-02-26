# Fizz Buzz  

[Question Link](https://leetcode.com/problems/fizz-buzz/)  

Write a program that outputs the string representation of numbers from 1 to n.  

But for multiples of three it should output “Fizz” instead of the number and for the multiples of five output “Buzz”. For numbers which are multiples of both three and five output “FizzBuzz”.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:
you can combine the two conditions by multiplying them

## Solution:
```Python
class Solution(object):
    def fizzBuzz(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        answer = []
        for num in xrange(1, n + 1):
            if num % 15== 0:
                answer.append("FizzBuzz")
                continue
            
            if num % 3 == 0:
                answer.append("Fizz")
                continue
                
            if num % 5 == 0:
                answer.append("Buzz")
                continue
                
            answer.append(str(num))
            
        return answer
```