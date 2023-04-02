---
title: 'The Missing Number - Easy'
date: 2013-04-09T00:36:00.002-07:00
draft: false
url: /2013/04/the-missing-number.html
tags: 
- computer science
- algorithm
- easy
- interview question
---

For my first post, let's start with an easy one. It's a popular question among interviewers and you prolly have heard about this one. Never the less, let's solve it, for old times sake. :)  
  

> _Problem : Given an Array of integers of size N. The array contains all the numbers from 1 to N in arbitrary order. But one number (say X) has been replaced with 0. Find the missing number in the most efficient way possible._

  
Solution:  
  
Before we get to the solution, we'll build a test case using the following Python Snippet.  
  
The Naive method is an O(n^2) algorithm, where we perform a linear search (ie O(n) ) for each element 1-N.  
For small values of N, this is perfectly fine but can we do better?  
  
Of course, with a small bit of help from 8th grade maths. Hopefully, you remember that,  

> 1+2+3....+n = n (n+1)/2

So how does that help? Say we didn't have any missing number and the problem was simply to sum all the elements of the array? Since we know the array contains all the values of the range \[1,N\] we know the sum will be _N \* (N + 1) /2 _  
If we replaced one arbitrary element with 0, the expected sum will be _(N \* (N + 1) / 2) - X  _  
But we can calculate the Expected sum by iterating through the array and adding all the elements, so we finally have  

> X = (N \* (N+1) / 2) - sum(array)

Here's the Python solution  
Now, the inbuilt _sum()_ function in Python is linear.  
  
This solution is perfectly fine for Python, but if we translate this to an High Level Language (HLL) like Java or C, you'll end up with this.  
Can you spot the problem with the above snippet? How will you solve it? Answer during the next update.  
  
_Update:_ Python supports arbitrary precision numbers by default, unlike Java. Therefore the above code might fail for Large values of N. More specifically N > sqrt(Integer.MAX\_VALUE). How do we solve it? Use a bigger datatype (long,BigInteger).  
  
**Alternate Solutions:**  
  
_Using a Hash Table/Bit Array_: This solution is quite obvious. Have a Bit Array of size N, Iterate over the array and mark true the index of the bit array for each value in the array. Find the only element that is false.  
Note: If there were multiple numbers missing, this will find all of them. So this is probably the best method for multiple missing numbers. We'll discuss other methods in the future.  
Space Complexity : O(n/8), Time : O(n)  
  
_The XOR method :_ This is pretty smart method and doesn't even have the possibility of Integer Overflows. The idea is we can determine (1^2^3....^N) in O(1). (see below) Say P = (1 ^ 2 ^ .... ^ N), we then Xor all the values in the Array which will be Q = (1^2^...(X-1)^(X+1)^....N)  
Our missing X = P ^ Q  
  
To find the the Xor result of the range 1 to N, we observe the following pattern.  
  

> N = 0, P= 0  
> 1,1  
> 2,3  
> 3,0  
> 4,4  
> .....  
> 84,84  
> 85,1  
> 86,87  
> 87,0  
> 88,88

  
  
The pattern repeats with a period of 4,  
  

1.  When N is divisible by 4, the Xored value is N itself
2.  When N % 4 is 1, the Xored value is 1
3.  When N % 4 is 2, the Xored value is N+1
4.  When N % 4 is 3, the Xored value is 0

Here's a small python snippet for the same. Time Complexity : O(n)

  

You can find the entire source code [here](https://github.com/st0le/lost-in-compilation/blob/master/missing_number.py).