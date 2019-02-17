# Keyboard Row  

[Question Link](https://leetcode.com/problems/keyboard-row/)  

Given a List of words, return the words that can be typed using letters of alphabet on only one row's of American keyboard like the image below.  

##### Constraints:

### Explanation:
TLDR: Break the rows into sets. Break each word into a set. Check each char in a word to be a subset of every row set. Initialize found to true on each row check and set false when char in word is not in row.

### Notes:


## Solution:
```Python
class Solution(object):
    def findWords(self, words):
        """
        :type words: List[str]
        :rtype: List[str]
        """
        
        top = set("qwertyuiop")
        mid = set("asdfghjkl")
        bot = set("zxcvbnm")
        
        rows = [top, mid, bot]
        
        answer = [];
        for word in words:
            chars = set(word.lower())
            
            found = False
            for row in rows:
                if found:
                    break
                else:
                    found = True
                    for c in chars:
                        if c not in row:
                            found = False
                            break;
            
            if found:
                answer.append(word)
        
        return answer
```