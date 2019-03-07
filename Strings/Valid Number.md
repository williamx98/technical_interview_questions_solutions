# Valid Number   

[Question Link](https://leetcode.com/problems/valid-number/)  

Validate if a given string can be interpreted as a decimal number.  

##### Constraints:

### Explanation:
TLDR: On every character, only a certain subset of characters are allowed to occur next. This uses a method called DFA, deterministic finite automaton.

The underlying algorithm for RegExp uses DFA.

### Notes:


## Solution:
```Python
class Solution(object):
    def isNumber(self, s):
        state = [{}, 
              {'blank': 1, 'sign': 2, 'digit':3, '.':4}, 
              {'digit':3, '.':4},
              {'digit':3, '.':5, 'e':6, 'blank':9},
              {'digit':5},
              {'digit':5, 'e':6, 'blank':9},
              {'sign':7, 'digit':8},
              {'digit':8},
              {'digit':8, 'blank':9},
              {'blank':9}]
        currentState = 1
        for c in s:
            if c >= '0' and c <= '9':
                c = 'digit'
            if c == ' ':
                c = 'blank'
            if c in ['+', '-']:
                c = 'sign'
            if c not in state[currentState].keys():
                return False
            currentState = state[currentState][c]
        if currentState not in [3,5,8,9]:
            return False
        return True
```