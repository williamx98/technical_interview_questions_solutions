# Top K Frequent Words

[Question Link](https://leetcode.com/problems/top-k-frequent-words/)  

Given a non-empty list of words, return the k most frequent elements.  

Your answer should be sorted by frequency from highest to lowest. If two words have the same frequency, then the word with the lower alphabetical order comes first.  

##### Constraints:

### Explanation:
TLDR: Use a modified bucket sort to search by word counts and not just words. This enables a sort time of O(n).

### Notes:


## Solution:
```Python
class Solution(object):
    def topKFrequent(self, words, k):
        class Node:
            def __init__(self):
                self.word = None
                self.children = [None] * 26

        def addToTree(word, root):
            for c in word:
                index = ord(c) - ord('a')
                if root.children[index] == None:
                    root.children[index] = Node()
                root = root.children[index]
            root.word = word

        def getWords(root, k, list):
            if root == None:
                return

            # Don't return on this statement.
            # For example if the word "foxy" and "fox" were both in the dictionary,
            # returning here would only capture "fox" and skip over "foxy"
            if root.word is not None:
                list.append(root.word)

            if len(list) == k:
                return

            for index in range(26):
                if root.children[index] is not None:
                    getWords(root.children[index], k, list)

        #get the counts for each word
        wordCounts = {}
        for word in words:
            if word in wordCounts:
                wordCounts[word] += 1
            else:
                wordCounts[word] = 1

        #get the words for each count
        countsWord = {}
        maxCount = 1
        for word in wordCounts:
            count = wordCounts[word]
            if count not in countsWord:
                countsWord[count] = Node()

            if maxCount < count:
                maxCount = count

            #based on the count, add to the tree at that count
            addToTree(word, countsWord[count])

        answer = []
        for count in range(maxCount, 0, -1):
            if count in countsWord:
                getWords(countsWord[count], k, answer)

        return answer
```