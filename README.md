# About

I know programming can be challenging so all my solutions are aimed at being simple and readable while preserving an optimized complexity. Feel free to make modifcations and update solutions when you find issues or improvements. 

Optimal solutions, in my opinion, are solutions that can be easily replicated in other languages so there are no fancy Python one-liner solutions. Most of these solutions will run at time and memory complexities better than 100% of the other solutions on LeetCode.

I try to avoid using small functions like min(), max(), and swap() because they abstract out certain foundational programming concepts I feel are important to show off especially to a recruiter or to someone who may not be familiar with Python or any language specific mehthods. I will use min(), max(), and swap() when I see that the solution is already cluttered. 

### Notes
##### The 'Mid Point' Bug
[Source article here](https://thebittheories.com/the-curious-case-of-binary-search-the-famous-bug-that-remained-undetected-for-20-years-973e89fc212)  
For 20 years there was a bug in most binary search, merge sort, or any kind of function that utilized the calculation of a mid-point value. In code, it looked like this:  
```mid = (low + high)/2```  
The problem with the code is that there is potential for overflow. If ```low``` were ```INT_MAX - 2``` and ```high``` were ```INT_MAX```, mathematically the mid-point would be ```INT_MAX - 1```. However, the order of operations forces the addtion of ```low``` and ```high``` first so ```low + high``` would be ```(2 * INT_MAX) - 2```. ```(2 * INT_MAX)``` would cause an integer overflow error and break the flow of the algorithm.  
  
To fix this, the code is:  
```mid = low (high - low)/2```  
This will offset the low value by half the difference between the high and low value. In short, this psuedo-reverses the order of operations of the original code, preventing and integer overflow.  



### Contact
If you find a bug, want to say thank you, or give me a job, my contact details are below:  

[Website: willx.org](https://willx.org)  
[LinkedIn: willx.org/linkedin](https://willx.org/linkedin)  
[GitHub: willx.org/github](https://willx.org/github)  
[Resume: willx.org/resume](https://willx.org/resume)  
