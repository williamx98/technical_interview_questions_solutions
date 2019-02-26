# 4Sum  

[Question Link](https://leetcode.com/problems/4sum/)  

Given an array nums of n integers and an integer target, are there elements a, b, c, and d in nums such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.  

##### Constraints:

### Explanation:
TLDR: Generate pairs and group the pairs by their sums. Then, go through each sum value, found the target value to make 0, and generate all combinations of the first list and the second list.  

### Notes:


## Solution:
```Python
class Solution:
    def fourSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        
        d = dict()
        for i in range(len(nums)):
            for j in range(i+1,len(nums)):
                sum2 = nums[i]+nums[j]
                if sum2 in d:
                    d[sum2].append((i,j))
                else:
                    d[sum2] = [(i,j)]
        
        result = set()
        for key in d:
            toGet = target - key
            if toGet in d:
                list1 = d[key]
                list2 = d[toGet]
                for (i,j) in list1:
                    for (k,l) in list2:
                    	# this is to ensure you are not referencing the same value twice. i.e a value occurs once but you use it twice.
                        if i!=k and i!=l and j!=k and j!=l:
                            flist = [nums[i],nums[j],nums[k],nums[l]]
                            flist.sort()
                            result.add(tuple(flist))
        return list(result)
```