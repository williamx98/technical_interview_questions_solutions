# Excel Sheet Column Title  

[Question Link](https://leetcode.com/problems/excel-sheet-column-title/)  

Given a positive integer, return its corresponding column title as appear in an Excel sheet.  

Input: 28  
Output: "AB"  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def convertToTitle(self, n):
        """
        :type n: int
        :rtype: str
        """
        
        def toChar(num):
            return chr(num + ord('A') - 1)
        
        answer = []
        while n > 0:
            digit = n % 26
            if digit == 0:
                digit = 26
                n -= digit
                
            answer.append(toChar(digit))
            n = n // 26
            
        return ''.join(answer[::-1])
            
            
```