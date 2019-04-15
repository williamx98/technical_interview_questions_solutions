# To Lower Case

[Question Link](https://leetcode.com/problems/to-lower-case)  

Implement function ToLowerCase() that has a string parameter str, and returns the same string in lowercase.

### Explanation:
TLDR: Use ASCII table values to convert between cases.

## Solution:
```Python
class Solution(object):
    def toLowerCase(self, str):
        """
        :type str: str
        :rtype: str
        """
        str = list(str)
        lowerOffset = (ord('a') - ord('A'))
        A = ord('A')
        Z = ord('Z')

        for index in range(len(str)):
            s = str[index]
            val = ord(s)
            if val >= A and val <= Z:
                str[index] = chr(val + lowerOffset)

        return ''.join(str)   
```
