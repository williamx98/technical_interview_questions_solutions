# Best Time to Buy and Sell Stock II  

### Rating: [3/5] Good intro into arrays. Somewhat convoluted. Straight forward solution.

[Question Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)  

Say you have an array for which the ith element is the price of a given stock on day i.  

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).  

Note: You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).  

### Explanation:
TLDR: Add to profit whenever there is a positive growth in price.

## Solution:
```Python
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        profit = 0
        
        for index in xrange(1, len(prices)):
            possibleProfit = prices[index] - prices[index - 1]
            if possibleProfit > 0:
                profit += possibleProfit
                
        return profit
```
