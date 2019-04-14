# Word Pattern  

[Question Link](https://leetcode.com/problems/word-pattern/)  

Given a pattern and a string str, find if str follows the same pattern.  

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.  

### Explanation:
TLDR: On a high level, you are looking for a 1:1 mapping between the letters and the words. Rather than make two dictionaries, make one dictionary and then a set of the values. If the letter is already in the dictionary, check if the word matches. If the letter is not in the dictionary, check if its in the values set.

```True```
```pattern = "abba", str = "dog cat cat dog"```
```dict = {a = dog, b = cat}    set = (dog, cat)```

```False```
```pattern = "abba", str = "dog cat cat fish"```
```dict = {a = dog, b = cat}    set = (dog, cat)```
```false because 'a' in dict but 'fish' != 'dog'```

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
