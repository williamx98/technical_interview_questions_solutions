# Reverse Words in a String III

[Question Link](https://leetcode.com/problems/reverse-words-in-a-string-iii/)  

Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.  

### Explanation:
TLDR: 

## Solution:
```Python
class Solution(object):
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """
        s = s.split(" ")
        
        for index in range(len(s)):
            s[index] = s[index][::-1]
        
        return " ".join(s)
```
