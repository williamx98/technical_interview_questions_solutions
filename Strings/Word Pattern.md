# Word Pattern  

[Question Link](https://leetcode.com/problems/word-pattern/)  

Given a pattern and a string str, find if str follows the same pattern.  

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def wordPattern(self, pattern, str):
        dict = {}
        used = set()
        
        words = str.split(" ")
        if len(words) != len(pattern):
            return False
        
        for i, p in enumerate(pattern):
            if p in dict:
                if dict[p] != words[i]:
                    return False
            else:
                if words[i] in used:
                    return False
                dict[p] = words[i]
                used.add(words[i])
            
        return True
```