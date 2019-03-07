# Best Time to Buy and Sell Stock  

[Question Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)  

Say you have an array for which the ith element is the price of a given stock on day i.  

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.  

Note that you cannot sell a stock before you buy one.  

##### Constraints:

### Explanation:
TLDR: Track the current min. Subtract the current min from the current value and assess if its greater than the default max profit of 0

### Notes:


## Solution:
```Python
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        maxProfit = 0
        currMin = None
        
        for price in prices:
            if currMin is None or price < currMin:
                currMin = price
            elif price - currMin > maxProfit:
                maxProfit = price - currMin
                
        return maxProfit
```