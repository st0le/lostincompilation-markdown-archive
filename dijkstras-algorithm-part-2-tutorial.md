---
title: 'Dijkstra''s algorithm - Part 2 - Tutorial'
date: 2013-05-05T13:34:00.002-07:00
draft: false
url: /2013/05/dijkstras-algorithm-part-2-tutorial.html
tags: 
- tutorial
- computer science
- python
- algorithm
---

  
For Part 2 of the series, we'll be developing a Priority Queue implemented using a [Heap ](http://en.wikipedia.org/wiki/Heap_(data_structure)). Continuing from [Part 1](http://lostincompilation.blogspot.com/2013/04/dijkstras-algorithm-part-1-tutorial.html), we'll be using Python for the implementation.  
  
Fortunately, Python has a [PriorityQueue](http://docs.python.org/2/library/queue.html#Queue.PriorityQueue) class in the \`queue\` module. It's more than enough for our purposes, but the Queue module was designed thread safe, so there is a small overhead that comes with it. The Priority Queue is a Minimum Priority Queue by default, it takes in tuples which are compared together to determine their position in the queue. For those unfamiliar with tuple comparison in Python, it works something like this.  

>   
> \>>> (1,2) < (3,4)  
> True  
> \>>> (1,2) < (1,3)  
> True  
> \>>> (1,2) < (1,1)  
> False  
> \>>> (1,2) < (1,2,3)  
> True  
> \>>> (1,2,3,4) < (1,2,3)  
> False

  
The first non equal element  of the both tuples determine the output of the comparison operation. So say you have a bunch of Tasks Ti with Priorities Pi, then we push (Pi, Ti) into the queue, the Queue will automatically order it such that the first element popped will be the one with the lowest priority value.  
  
Here's an example showing this in Action.

Now, what if we wanted the priority queue to work in the reverse order (ie, Largest Value has the higher Priority)? Well, there isn't any feature provided for this by the module, but we can do a [clever little hack](http://lostincompilation.blogspot.com/2013/04/puzzle-sorting-3-integers.html), observe when we negate the priority the output of the comparison operation flips. Therefore, For a Maximum Priority Queue, simply insert (- Pi, Ti)....and presto, now the elements are ordered by decreasing order of priority.  
  
For the sake of learning, we'll implement our own Priority Queue. Using a heap for a backend implementation. Python comes with the [heapq](http://docs.python.org/2/library/heapq.html) module. The heapq module lets us use a list as a heap, it has the _heappush_ and _heappop_ functions push an element onto a heap. The comparison of the elements work as  before with the Priority Queue.  
  
Here's the class I wrote, it has a priority-tie-breaking mechanism. I simply add a counter as the second element to the tuple, this is essential for two things. One, when two elements have the same priority, the one inserted first will be popped first. Second, if we don't add this, then we'll have to make the data-elements comparable otherwise python will attempt to compare 2 elements (possibly non-comparable) with 2 equal priorities. In order to avoid this, we introduce the counter. So the Tuple Comparison will be resolved at the counter itself. Also, I've abstracted the min/max priority by having the pqueue class take care of negating the priorities. Far more convenient in my opinion.  
  
Here's the complete [source code](https://github.com/st0le/lost-in-compilation/blob/master/pqueue.py).  
  
We now have the essential tools for implementing our Dijkstra's Shortest Path algorithm. Until next time...