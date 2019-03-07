# Plus One  

[Question Link](https://leetcode.com/problems/plus-one/)  

Given a non-empty array of digits representing a non-negative integer, plus one to the integer.  

The digits are stored such that the most significant digit is at the head of the list, and each element in the array contain a single digit.  

You may assume the integer does not contain any leading zero, except the number 0 itself.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def plusOne(self, digits):
        carry = 1
        
        index = len(digits) - 1
        while index >= 0 and carry == 1:
            digits[index] += carry
            if digits[index] >= 10:
                carry = digits[index] % 9
                digits[index] %= 10
            else:
                carry = 0
            index -= 1
            
        if carry == 1:
            digits.insert(0, carry)
        return digits
```