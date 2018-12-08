# Welcome to my collection of solutions to technical questions!
Here, you will find solutions to techinical questions that I have used as I prepare for technical interviews using various sites such as LeetCode and HackerRank.

Solutions are separated by the question type.  

Within seach solutions file, you will find the 2 verions of the solution: one with comments, one without.  
You will also find a README of the question and the source link to the question.  

---

## Design Philosophy
#### KISS: Keep It Stupid Simple
My goal is always to make a solution that is dead simple often relying heavily on fundamentals and avoiding the use of built-in libraries when possible. For example, instead of using:
```
max = Math.max(max, current_value)
```  
I will use:  
```
if current > max: max = current
```

Personally, using the `if` conditional is more clear as to what the code is doing, which is to update the maximum value, and it's a lot faster reading-wise as well.  

You'll notice that using the `if` conditional puts the conditional check first in the line. That way, your mind doesn't have to temporarily remember what variable is being updated after trying to evaluate what it is being updated to i.e is it updating to max or updating to min? The decision to read the inner code of the conditional can be evaluated quickly as the conditional determines whether it is relevant or not. If the conditional is false, the inner block can be safely ignored.

Also, it is mathematically and syntactically clear as to under what conditions the current value is to be updated and if it needs to be updated at all. While this particular example is simple and the difference is minimal, small design choices like this help make code more clear and concise as solutions become more complicated.

Also also, by avoiding the use of built-ins for specific languages, solutions are "universal" in that the solution can easily be translated into other languages as there are no language-specific functions in the solution. 

Of course, this also helps to keep programs smaller in size as the more imports are necessary, the more extraneous class variables and methods are included as a part of the file.

Also also also, solutions will often be at the optimal solution, where time complexity is at its fastest and space complexity is at its lowest.

#### To recurse or to not recurse
I have been told that those who learn recursion first, have trouble understanding iterative solutions while those who learn iteration first, have trouble understanding recursive solutions. Now, I am not all too sure how true that is for everyone but, I know this is the case for me. I have never actually met anyone who has learned recursion first before learning iteration...

I am of the iteration-first class of people so I often have trouble understanding and making recursive solutions. I understand that syntactically, recursive solutions can be much more concise and elegant but, my mind just isn't able to keep track of the different calls and the overall stack sometimes. 

However, just because I have trouble with recursion doesn't mean I don't want to understand it. Recursion is often used in interview questions and having a firm understanding of recursion is a key fundamental of computer science so as a part of the solution, I will often include both iterative and recursive solutions.

## Contact
If you find a bug, want to say thank you, or give me a job, my contact details are below:  
[LinkedIn: linkedin.com/in/willx98] (https:linkedin.com/in/willx98)  
[GitHub: github.com/willx98] (https://github.com/willx98)  
[website: willxu.site] (https://willxu.site)