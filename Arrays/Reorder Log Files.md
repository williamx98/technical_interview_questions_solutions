# Reorder Log Files  

[Question Link](https://leetcode.com/problems/reorder-log-files/)  

This question has terrible wording. It also is just a terrible question in general.  

You have an array of logs.  Each log is a space delimited string of words.  

For each log, the first word in each log is an alphanumeric identifier.  Then, either:  

Each word after the identifier will consist only of lowercase letters, or;  
Each word after the identifier will consist only of digits.  
We will call these two varieties of logs letter-logs and digit-logs.  It is guaranteed that each log has at least one word after its identifier.  

Reorder the logs so that all of the letter-logs come before any digit-log.  The letter-logs are ordered lexicographically ignoring identifier, with the identifier used in case of ties.  The digit-logs should be put in their original order.  

Return the final order of the logs.  


##### Constraints:

### Explanation:
TLDR: 

### Notes:


## Solution:
```Python
import heapq
class Solution(object):
    def reorderLogFiles(self, logs):
        """
        :type logs: List[str]
        :rtype: List[str]
        """
        digit = []
        letter = []
        
        for log in logs:
            delimit = log.split(" ")
            try:
                int(delimit[1])
                digit.append(log)
            except:
                heapq.heappush(letter, (log[log.find(" ") + 1:], delimit[0], log))
            
        letter = heapq.nsmallest(len(letter), letter)
        
        for index in range(len(letter)):
            letter[index] = letter[index][2]
        letter.extend(digit)
        return letter
        
```