---
title: 'Find the Triple - Hard'
date: 2013-07-01T14:44:00.000-07:00
draft: false
url: /2013/07/find-triple-hard.html
tags: 
- hard
- computer science
- algorithm
- interview question
---

> Problem : Given 3 Integer Arrays A,B,C. Find out if an instance exists where A\[i\] + B\[j\] + C\[k\] == 0.

  
Very deceptive question but very similar to the [3SUM](http://lostincompilation.blogspot.com/2013/06/3sum-hard.html) Problem. The Naive solution is O(n^3). If you're a little clever, you can do a O(n^2 logn). At this point, you might give up assuming that this is pretty efficient. But then there is also a O(n^2) solution as well!  
  
Let's go from worst to best.  
  
The Naive solution is trivial.  
Try every combination until we hit a solution, if we don't there is no solution.  
  
So let's try to speed things up a bit, since the solution is already O(n^3), I think we can afford to sort any of the  arrays since nlogn = o(n^3). Therefore, we cleverly sort the Array C. Now in the third loop we replace the linear scan with a binary search to find (-A\[i\]-B\[j\]). The complexity is now reduced to O(n^2 logn)  
  
At this point, you've leveled up. The next algorithm might not be immediately apparent but works. In fact the method is similar to the O(n^2) solution to 3SUM.  
  

Java Code for all these solutions can be found [here.](https://github.com/st0le/lost-in-compilation/blob/master/FindTriplet.java)