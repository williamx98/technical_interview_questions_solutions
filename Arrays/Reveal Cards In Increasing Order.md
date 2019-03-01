# Reveal Cards In Increasing Order  

[Question Link](https://leetcode.com/problems/reveal-cards-in-increasing-order/)  

In a deck of cards, every card has a unique integer.  You can order the deck in any order you want.  

Initially, all the cards start face down (unrevealed) in one deck.
  
Now, you do the following steps repeatedly, until all cards are revealed:  
  
Take the top card of the deck, reveal it, and take it out of the deck.  
If there are still cards in the deck, put the next top card of the deck at the bottom of the deck.  
If there are still unrevealed cards, go back to step 1.  Otherwise, stop.  
Return an ordering of the deck that would reveal the cards in increasing order.  
  
The first entry in the answer is considered to be the top of the deck.  

### Explanation:
TLDR: use an inorder array to be shuffled into that order. simulate the alogrithm by performing each op on the inorder array which will now be altered in the form of the array. 

## Solution:
```Python
class Solution(object):
    def deckRevealedIncreasing(self, deck):
        """
        :type deck: List[int]
        :rtype: List[int]
        """
        indexes = collections.deque()
        answer = []
        for index in xrange(len(deck)):
            answer.append(None)
            indexes.append(index)
            
        deck.sort()
        
        for card in deck:
            answer[indexes.popleft()] = card
            if indexes:
                indexes.append(indexes.popleft())
                
        return answer
        
```
