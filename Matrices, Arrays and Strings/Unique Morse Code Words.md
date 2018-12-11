# Unique Morse Code Words

[Question Link](https://leetcode.com/problems/unique-morse-code-words/)  

International Morse Code defines a standard encoding where each letter is mapped to a series of dots and dashes, as follows: "a" maps to ".-", "b" maps to "-...", "c" maps to "-.-.", and so on.  

For convenience, the full table for the 26 letters of the English alphabet is given below:  

```Python
[".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
``` 

Now, given a list of words, each word can be written as a concatenation of the Morse code of each letter. For example, "cba" can be written as "-.-..--...", (which is the concatenation "-.-." + "-..." + ".-"). We'll call such a concatenation, the transformation of a word.  

Return the number of different transformations among all words we have.  

##### Constraints:

### Explanation:

### Notes:


## Solution With Comments:
```Python
class Solution(object):
    def uniqueMorseRepresentations(self, words):
        """
        :type words: List[str]
        :rtype: int
        """
        uniqueTransformations = set()
        letterToMorse = [".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
        a = ord('a')
        
        for word in words:
            morseTrans = []
            for c in word:
                index = ord(c) - a
                morseTrans.append(letterToMorse[index])
            uniqueTransformations.add(''.join(morseTrans))
        
        return len(uniqueTransformations)
    
```
