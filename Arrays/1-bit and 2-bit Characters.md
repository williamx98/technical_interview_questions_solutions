# 1-bit and 2-bit Characters  

### Rating: [0/5] Convoluted question. Not useful to study in my opinion 

[Question Link](https://leetcode.com/problems/1-bit-and-2-bit-characters/)  

We have two special characters. The first character can be represented by one bit 0. The second character can be represented by two bits (10 or 11).  

Now given a string represented by several bits. Return whether the last character must be a one-bit character or not. The given string will always end with a zero.  

### Explanation:
To help avoid confusion, an individual item of the given bits array will be called a *bit*. *Characters* will be the 1 or 2 bit characters as explained in the problem statement.

This question is pretty confusing but, the solution is easy to understand once you understand what the question is asking: **reading the bits from left to right, must the last decoded character be a 1-bit character**.

Another way to go about this is, **is it *possible* to end the bits array with a 2-bit character**

So let's break down some examples and possible cases.

We know our base-cases:  
```0``` is true. ```[0]```  
```10``` is false. ```[10]```  
```00``` is false. ```[00]```  

What about further cases?  

```000``` is true. ```[0] [0] [0]```  
```010```  is false. ```[0] [10]```  
```100```  is true. ```[10] [0]```  
```110```  is true. ```[11] [0]```  
```1000```  is false. ```[10] [00]```  
```1010```  is true. ```[10] [10]```  
```1100```  is true. ```[11] [0] [0]```  
```1110```  is false. ```[11] [10]```  
```0000```  is true. ```[0] [0] [0] [0]```  
```0010```  is false. ```[0] [0] [10]```  
```0100```  is true. ```[0] [10] [0]```  
```0110```  is true. ```[0] [11] [0]```  

This isn't very helpful and a pattern isn't immediately obvious so let's sort these results by number of characters.

1 character:  
[1 bit]  
```0``` is true. ```[0]```  
[2 bits]  
```10``` is false. ```[10]```  
```11``` is not valid. Does not end in ```0```  

2 characters:  
[1 bit], [1 bit]  
```00``` is true. ```[0] [0]```  
[1 bit], [2 bits]  
```010```  is false. ```[0] [10]```  
[2 bits], [1 bit]  
```100```  is true. ```[10] [0]```  
```110```  is true. ```[11] [0]```  
[2 bits], [2 bits]  
```1010``` is false. ```[10] [10]```  
```1110``` is false. ```[11] [10]```  

3 characters:  
[1 bit], [1 bit], [1 bit]  
```000``` is true. ```[0] [0] [0]```  
[1 bit], [1 bit], [2 bits]  
```0010```  is false. ```[0] [0] [10]```  
[1 bit], [2 bits], [1 bit]  
```0100```  is true. ```[0] [10] [0]```  
```0110```  is true. ```[0] [11] [0]```  
[2 bits], [1 bit], [1 bit]  
```1000```  is true. ```[10] [0] [0]```  
```1100```  is true. ```[11] [0] [0]```  
...  
[1 bit], [2 bits], [2 bits]  
```01010``` is false. ```[0] [10] [10]```  
```01110``` is false. ```[0] [11] [10]```  

* Notice that every break down that ends in ```[0] [0]``` is true.
* Notice that in every break down, ```0```s are at the end of characters (but not all characters end in ```0```)
* Notice that in 3 character break downs that end in a corresponding 2 character break down, the results are the same. For example.
 - For example: ```0110```  breaks down (```[0] [11] [0]```) which ends in ```110``` (```[11] [0]```) and they are both true.
* Notice that in 2-bit characters, you can subsitute ```[10]``` with ```[11]``` and still get the same result. 
 - For example: ```1010``` (```[10] [10]```) and ```1110``` (```[11] [10]```) are both false.

Admittedly, its still not very obvious but if you look at the true results, the number of ```1```s between the last two ```0```s is even.
* ```00``` is true. ```[0] [0]```. There are zero ```1```s
* ```0110```  is true. ```[0] [11] [0]```. There are two ```1```s

if you look at the false results, the number of ```1```s between the last two ```0```s is odd.
* ```010```  is false. ```[0] [10]```. There is one ```1```
* ```01110``` is false. ```[0] [11] [10]```. There are three ```1```s

So let's think about what we can infer from this:

* Since a 1-bit character is ```0``` and a 2-bit character is ```10``` or ```11```, whenever we encounter a ```0```, that is the end of any *kind* of character (1-bit or 2-bit).

* Since a ```0``` ends a character, the next *bit* will be the start of the next character (but we don't know what kind, 1-bit or 2-bit).

Now that we know when characters can end and when characters can start, how do we simplify the solution-space?

Since we know that any given ```0``` ends a character, that means that all other bits before that ```0``` "don't really matter".
i.e no matter how the bits are interpretted up to a given ```0```, a character ends at that given ```0```, everytime.

What really matters then, is the number of consecutive ```1```s between the last two ```0```s.

* If the number of consecutive ```1```s between the *second-to-last* and *last* ```0``` is **odd**, then the last character must be read as a 2-bit character.

* If the number of consecutive ```1```s between the *second-to-last* and *last* ```0``` is **even**, then the last character must be read as a 1-bit character.

There are many ways to count the number of something but, since we only care about count's parity (if it is even or odd), we only need to keep track of the parity itself.

If we use a counter and then dervive the parity from the counter, we run the risk of overflowing the counter if the length of the bits array exceeds the maximum limit of the counter's data type. Of course, this is not a concern given the problem constraints but, it is always good to keep in mind the robust-ness of your solutions.

## Solution:
```Python
class Solution(object):
    def isOneBitCharacter(self, bits):
        """
        :type bits: List[int]
        :rtype: bool
        """
        parity = 1
        i = len(bits) - 2
        while i >= 0 and bits[i] != 0:
            parity ^= bits[i]
            i -= 1

        return parity
```
