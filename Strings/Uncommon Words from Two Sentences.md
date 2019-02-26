# Uncommon Words from Two Sentences  

[Question Link](https://leetcode.com/problems/uncommon-words-from-two-sentences/)  

We are given two sentences A and B.  (A sentence is a string of space separated words.  Each word consists only of lowercase letters.)  

A word is uncommon if it appears exactly once in one of the sentences, and does not appear in the other sentence.  

Return a list of all uncommon words.   

You may return the list in any order.  

##### Constraints:

### Explanation:
TLDR: an uncommon word only appears in one of the sentences, combine them together and count each word occurence.

### Notes:


## Solution:
```Python
class Solution(object):
    def uncommonFromSentences(self, A, B):
        """
        :type A: str
        :type B: str
        :rtype: List[str]
        """
        A = A.split(" ")
        A.extend(B.split(" "))
        counts = {}
        for a in A:
            counts[a] = 1 if a not in counts else counts[a] + 1
        
        answer = []
        for key in counts:
            if counts[key] == 1:
                answer.append(key)
        
        return answer
```