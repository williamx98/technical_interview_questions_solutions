# Best Time to Buy and Sell Stock  

### Rating: [4/5] Good intro into greedy algorithms. Kind of confusing if you don't understand how stocks work.

[Question Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)  

Say you have an array for which the ith element is the price of a given stock on day i.  

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.  

Note that you cannot sell a stock before you buy one.  

### Explanation:
TLDR: Track the current min. Subtract the current min from the current value and assess if its greater than the default max profit of 0.

To find a globally optimal buy-day and sell-day pair, we need compare the profits of every pair of valid buy-days and sell-days. Valid buy-day and sell-day pairs are defined as buy days that are paired with later sell days.  

This will give us the answer but the work performed is not optimal.  

In stock trading, we can not see the future so what we need to do is simulate days passing by traversing the array and only working with the the information we have of previous days up to the current day. 

On the current day, we can either buy or sell but since we are looking for the best buy-sell day pair, we buy on the current day if today is lowest price we have seen. If the current day is not the lowest price we have seen, that implies we bought earlier and so we should see how much money we can make by selling today and seeing if we could make more money than if we sold earlier.

The optimization here is to compare the current day to the lowest price so far. Instead of comparing each earlier day to the current day, an O(n) operation, we are only comparing one buy day to the current day, an O(1) operation.


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
            else:
                maxProfit = max(price - currMin, maxProfit)
                
        return maxProfit
```
