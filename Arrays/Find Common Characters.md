# Find Common Characters  
## Rating: [5/5] Straight forward question. Straight foward solution. Good practice for hashmaps/dictionaries

[Question Link](https://leetcode.com/problems/find-common-characters/)  

Given an array A of strings made only from lowercase letters, return a list of all characters that show up in all strings within the list (including duplicates).  For example, if a character occurs 3 times in all strings but not 4 times, you need to include that character three times in the final answer.  

You may return the answer in any order.  

##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
class Solution(object):
    def commonChars(self, A):
        """
        :type A: List[str]
        :rtype: List[str]
        """
        answer = None
        
        for a in A:
            # create the counts for the current word
            work = {}
            for c in a:
                if c in work:
                    work[c] += 1
                else:
                    work[c] = 1
            
            # compare the current word counts
            # keep the least of the common ones
            # delete the ones in the answer not found in the current word
            if answer != None:
                keys = list(answer.keys())
                for k in keys:
                    if k in work:
                        answer[k] = min(answer[k], work[k])
                    else:
                        del answer[k]
            else:
                answer = work

        # turn the counts into an array
        answerArr = []
        for key in answer:
            count = answer[key]
            for _ in xrange(count):
                answerArr.append(key)
        
        return answerArr
```