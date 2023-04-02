---
title: 'Find the Quadruplets - Hard'
date: 2013-07-01T16:47:00.003-07:00
draft: false
url: /2013/07/find-quadruplets-hard.html
tags: 
- hard
- computer science
- algorithm
- interview question
---

  

> Problem - Given 4 arrays A,B,C,D. Find out if there exists an instance where A\[i\] + B\[j\] + C\[k\] + D\[l\] = 0

  
Like the [Find the Triple](http://lostincompilation.blogspot.com/2013/07/find-triple-hard.html) problem, we're going to develop 4 algorithms to solve this. Starting with the naive O(n^4) solution.

  
Then we proceed to eliminate the inner-most loop with a Binary Search, reducing the complexity to O(n^3 logn)  
  
Now, we replace the last 2 loops with the left-right traversal we did in the previous 3 posts.  
  
Now the complexity is O(n^3).  
  
Finally, we reduce the complexity to O(n^2 logn) at the cost of O(n^2) Space Complexity. We store every combination of A\[i\] + B\[j\] and store it in AB\[\]. Similarly we make CD\[\] out of C\[i\] + D\[j\].  
  
  
So,  
  
AB = A x B  
CD = C x D  
  
We then sort AB and CD (which costs O(n^2 log(n^2)) ~ O(n^2 logn) ) and then run a left-right linear Algorithm on AB and CD. (Note : Their size is of the order O(n^2))  
  
So the overall complexity is due to sorting the large array of size n^2. which is O(n^2 logn).