# Shuffle an array 

[Question Link](https://leetcode.com/problems/shuffle-an-array/)  

Shuffle a set of numbers without duplicates.  

### Explanation:
TLDR: for every item, pick a random index in the array and swap with that index

## Solution:
```Python
class Solution(object):

    def __init__(self, nums):
        """
        :type nums: List[int]
        """
        self.data = nums

    def reset(self):
        """
        Resets the array to its original configuration and return it.
        :rtype: List[int]
        """
        return self.data

    def shuffle(self):
        """
        """
        Returns a random shuffling of the array.
        :rtype: List[int]
        """
        copy = list(copy)
        for i in range(len(copy)):
            # pick a random index
            swap = random.randrange(i, len(copy))
            
            # swap current index with the random index
            temp = copy[swap]
            copy[swap] = copy[i]
            copy[i] = temp
            
        return copy
```
