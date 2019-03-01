# Number of Recent Calls

[Question Link](https://leetcode.com/problems/number-of-recent-calls/)  
Write a class RecentCounter to count recent requests.  

It has only one method: ping(int t), where t represents some time in milliseconds.  

Return the number of pings that have been made from 3000 milliseconds ago until now.  

Any ping with time in [t - 3000, t] will count, including the current ping.  

It is guaranteed that every call to ping uses a strictly larger value of t than before.  

### Explanation:
TLDR: On every ping, find the timestamp for which an earlier pings should be deleted.  

## Solution:
```Python
class RecentCounter(object):
    
    def __init__(self):
        self.queue = []

    def ping(self, t):
        """
        :type t: int
        :rtype: int
        """
        self.queue.append(t)
        while self.queue[0] < t - 3000:
            del self.queue[0]
        
        return len(self.queue)
```
