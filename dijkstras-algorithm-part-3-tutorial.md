---
title: 'Dijkstra''s algorithm - Part 3 - Tutorial'
date: 2013-05-14T00:01:00.002-07:00
draft: false
url: /2013/05/dijkstras-algorithm-part-3-tutorial.html
tags: 
- tutorial
- computer science
- python
- algorithm
---

Here's [Part 1](http://lostincompilation.blogspot.com/2013/04/dijkstras-algorithm-part-1-tutorial.html) and [Part 2](http://lostincompilation.blogspot.com/2013/05/dijkstras-algorithm-part-2-tutorial.html)  
  
And now for the third and final part of the tutorial. We'll be implementing the actual algorithm here. But before we get started, let's go over some theory.  
  
Dijkstra's Shortest Path Algorithm, (V - Number of Vertices, E - Number of Edges)  
  

*   Applies to both Directed graph and Undirected graphs.
*   Greedy Algorithm. Always picks the local minimum to extend it's solution.
*   Uses Dynamic Programming. Stores solutions from _source_ to every other vertex on the shortest path to the _destination._
*   Edges cannot be negative.
*   Original Implementation by Dijkstra was O(V2) since it did not use a Minimum Priority Queue. _Tarjan & Fredman_ introduced the modern version of the algorithm using a Fibonacci Heap to pick the vertex closest to the source. The Complexity thus became O(E + V logV). 
*   Using a Binary Heap instead of a Fibonacci Heap increases the complexity to  O( (E+V) log V).

  

Variations. There are two variants of the algorithm, there is a subtle difference between them. The first one, you'll traditionally find in textbooks requires your heap to implement the DECREASE-KEY function to change the priority of an arbitrary vertex. The second variant works by reinserting vertices into the priority queue. In this variant, the queue might have the same node with different distance to the _source,_ which is wasteful of course. Without the function it might cost more in terms of space and performance. But for small graphs, both work more or less the same for Binary Heap/Binomial Heap. If we use a Fibonacci Heap, the first variant is more efficient. [Here's](http://stackoverflow.com/questions/9255620/why-does-dijkstras-algorithm-use-decrease-key) a good discussion about the difference on these two variations.

  

Our [pqueue](https://github.com/st0le/lost-in-compilation/blob/master/Dijkstra%20Tutorial/pqueue.py) implementation doesn't have the decrease-key method and is also implemented as a Binary Heap, so we'll be using the second variant.

  
The algorithm begins with a couple of auxiliary data structures which can be implemented by a vanilla dictionary (an array if the vertices are represented as positive integers).  
  
The first is the _distance,_ where _distance\[v\]_ denotes the minimum distance from _src_ to _v._  
The second is the _previous_ (or _parent_), where _previous\[v\] = u,_ denotes that the predecessor to _v_ on the shortest from _src_  to _v_ is _u._ This is required only if you're interested in the path from the source to the destination. Otherwise, the algorithm can work without it.  
  
Initially, _distance_ only has a single entry_. distance\[src\] = 0_, which is trivial. _previous\[src\] _ is populated  by a sentinel value (like NULL or -1). Since the path starts from _src_ itself!  
  
Here's my humble implementation of the algorithm in Python.  
  
Let's break it down.  

  
The first part is the initialization of the Algorithm, I simply add details about the source into the _distance_ and _previous_ dictionary. I proceed to then push a tuple into a [minimum priority queue](http://lostincompilation.blogspot.com/2013/05/dijkstras-algorithm-part-2-tutorial.html) (Part 2). The priority is based on the distance of the vertex from the _source._ Initially, we're pushing the _source_ itself, therefore _(0, src)_ is our first vertex to be processed.  
  
This is the main shebang of the algorithm. The while loop keeps processing entries in the priority queue until it's exhausted. With each iteration, new vertices are added to the queue when we find a better a path from _source_ to that vertex. Note, initially we've assumed the distance is infinity effectively, therefore every reachable vertex will be processed at least once. We find the vertex which is closest to the source, say _u_, at that point of time. We iterate through the adjacent vertices, say _v\_i_ and find out if a transit route through u is less costly than a direct route from _src_ to _v\_i. _  
  

> Is cost(src->u->v\_i ) < cost(src->v\_i)? 

> This is essentially, cost(src->u) + cost(u->v\_i) < cost(src->v\_i)

If it is true for any _v\_i,_  we "relax" that edge. Effectively, routing any transit to _v\_i_ through _u._ We update _distance_ and _previous_ for _v\_i_ and also push it into the priority queue for future iterations of the while loop. If we were using the first variant of the algorithm, we'd be using the _decrease-key_ instead of pushing a new entry into the priority queue.  
  
The final part is to simply backtrack the _previous_ dictionary from the destination back the source. This will essentially give us the shortest path from _source_ to _destination_ in the reverse order.  
  
I'll also post a mirror of the animation for the entire algorithm cycle from Wikipedia here. (incase it's ever taken down.)  

[![](http://3.bp.blogspot.com/-_AZ_EAfl6uM/UZHg_GrVPsI/AAAAAAAABlE/yxmUECwyVrs/s1600/Dijkstra_Animation.gif)](http://3.bp.blogspot.com/-_AZ_EAfl6uM/UZHg_GrVPsI/AAAAAAAABlE/yxmUECwyVrs/s1600/Dijkstra_Animation.gif)

  
  
Well, That's about it, Dijkstra's Shortest Path algorithm in Python. You'll find all the code relevant to the tutorial over [here.](https://github.com/st0le/lost-in-compilation/tree/master/Dijkstra%20Tutorial) Hope you've enjoyed the series and it helped you understand this beautifull algorithm better. Please leave any suggestions/improvements/corrections you have in the comment sections. Cheers!