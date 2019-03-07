# Length of Last Word  

[Question Link](https://leetcode.com/problems/length-of-last-word/)  

Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.  

If the last word does not exist, return 0.  

Note: A word is defined as a character sequence consists of non-space characters only.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def lengthOfLastWord(self, s):
        beginning = len(s) - 1
        offset = 0
        
        while beginning >= 0 and s[beginning] == ' ':
            offset += 1
            beginning -= 1
        
        while beginning >= 0 and s[beginning] != ' ':
            beginning -= 1
            
        beginning += 1
        
        return len(s) - beginning - offset
```