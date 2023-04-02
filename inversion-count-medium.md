---
title: 'Inversion Count - Medium'
date: 2014-08-29T22:17:00.000-07:00
draft: false
url: /2014/08/inversion-count-medium.html
tags: 
- computer science
- python
- algorithm
- medium
---

> Given an Array A\[1..n\] of distinct integers find out how many instances are there where A\[i\] > A\[j\] where i < j. Such instances can be called Inversions.

  

Say, \[100,20,10,30\] the inversions are (100,20), (100, 10), (100,30), (20,10) and the count is of course 4

  

The question appears as an exercise in the  Chapter 4 of [Introduction to Algorithms](http://www.amazon.com/Introduction-Algorithms-Thomas-H-Cormen/dp/0262033844).  (3rd Edition)

  

As per our tradition we'll start with the worst algorithm and incrementally improve upon it. So on with it.  
  
So the complexity of the algorithm is O(n^2). We can do this even faster using divide and conquer, more aptly if we use a variation of [Merge Sort](http://en.wikipedia.org/wiki/Merge_sort). To do this, unfortunately, we will have to mutate the array.  

  

The key to the algorithm is to understand that in an ascending sorted array the inversion count is zero. Say \[10,20,30\]

  

If we perhaps have an element 100 before the rest of the array, the inversion count becomes 3. \[100,10,20,30\]. If we placed the 100 at the second position the inversion count would be 2, \[10,100,20,30\].

  

So here's what we're going to do, we write a recursive function which returns inversion count. The function first recursively does it for the first half and second half of the array, the byproduct of these recursive calls is that both half's become sorted. (Just like Merge Sort!) Now if you have two sorted Arrays which should be merged into one, we can piggy back on the merging process (of merge sort!) and count the inversions by merely counting the number of times an element from the first half was greater than the element in the second half.

  

An example, for those who found my explanation confusing.

  

Say, at some point of the recursion, we have the following

First half : \[20,40,60,80\] , Second half : \[10,30,50,70\]

  

If you recall the merge subroutine, we first compare 20 and 10, since 20 > 10, that counts as an inversion. But also note, since the first half is sorted therefore it is guaranteed that  \[20, 40, 60, 80\] will all be greater than 10. Since 20 had to be the minimum element of the first half. Therefore the inversion count for 10 in this instance becomes 4 (size of the unexplored first half). Important to note, this algorithm only works if the integers are all distinct.

  

Speaking generally, let's say i is the index for first half, j is the index for the second. Aux is the auxillary array to store the result. Then,  
  

> If A\[i\] > A\[j\] then    // implies A\[j\] < A\[i…mid\]  
>     invCount = mid - i + 1  
>     Aux\[k++\] = A\[j++\]  
> Else  
>     Aux\[k++\] = A\[i++\]  
> End If

  

Now for the code, notice it's uncanny resemblance to merge sort.

  

And that's Inversion Count! :)