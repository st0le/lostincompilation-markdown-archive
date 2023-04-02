---
title: 'Bidirectional Dijkstra - Tutorial'
date: 2013-07-16T22:55:00.004-07:00
draft: true
url: 
tags: 
- tutorial
- computer science
- python
- algorithm
---

  
In this post, I'm going to briefly explain how to perform a bidirectional dijkstra's single-source-shortest-path algorithm. To begin with let me first be clear that, performing a bidirectional search does not improve the complexity of the algorithm. The bidirectional search is ideal when you want to find the shortest path between a source and a _single_ destination.  
  
You should probably be already familiar that, the original algorithm finds the shortest path to _every other vertex._ But in the real world, we usually want to know the shortest path between two vertices. Now, there's a small optimization we can perform when searching for a path to a source. When the _target_ vertex has been popped from the Priority Queue, we can exit out of the loop without processing the rest of the vertices. Because at this point we know the shortest path from the _source_ to _target._ There can be no other path to the target that can be accomplished using the remaining vertices. Note : Line 10.  
  
  

> **<**rant**\>** I've seen many implementations on the internet that try to be clever. They exit the loop as soon as we encounter the _target_ during the RELAX operations. This is incorrect. You'll get a wrong answer if you do this. **</**rant**\>**

  
The bidirectional approach lets us prune off unnecessary vertices and exit early as soon as we find the shortest path between the _source_ and _target_. We don't need to perform additional computations that don't add to the solution.  
  
This post is being written after watching this excellent lecture (Courtesy of MIT's OpenCourseware). I suggest you watch it first.  
  

  
Okay, so hopefully at this point you've watched the video, I'll try to reiterate the gist of the Algorithm.  
  
The Algorithm works in two directions, one in the forward direction from _source_ to _target_ (I'll refer this to FI for Forward Instance) and then one instance in the reverse/backward direction, _target_ to _source_ (here on called BI for Backward Instance). Both these instances run parallely and each instance has it's own Priority Queue and the other underlying data structures (_d_ and _Pi_) required for Dijkstra. At some point in the algorithm, we will encounter a vertex '_w_' that has been _**processed\***_ by both FI and BI. This is our termination condition. When we encounter _'w',_ we need to find a vertex _'k'_ (from all the _**visited\*\***_ vertices by both FI and BI) which gives us the best path from _source _to _target_ by having _k_ as an intermediate vertex.  
  
At this point, let me explain what's the difference between a _processed_ vertex and a _visited_ vertex.  

>   
> \*A vertex can be considered processed when it has been popped from the Priority Queue at least once. (Remember the the second variant of the algorithm can pop the same vertex multiple times.)  
> \*\*A _visited_ vertex is simply a vertex that is adjacent to a _processed_ vertex and is pushed into the Priority Queue but not Popped yet.

  
So now that we know the path from _source_ to _k_ from FI and path from _k_ to _target_ using the BI, we can append both these paths to get the path from _source_ to _target._ We simply iterate over all the vertices that was visited by both FI and BI and find the vertex _k_ which minimizes the path weight if we consider it as part of the path. Note : _k_ is not necessarily _w_  
An important thing I left out in the beginning, for a directed graph it's not possible to run a BI since we're traversing backwards from _target_ to _source._ Hence,the edges have to be reversed for BI. You might have to create a reversed copy of the graph. An undirected graph will not have this problem.

  
Here's my implementation, not exactly optimized. I'm sure there are ways to save some space but I aimed for readability since this is a tutorial.  
The Dijkstra's Tutorial Files have been updated with Bidirectional Search as well. Find it [here](https://github.com/st0le/lost-in-compilation/tree/master/Dijkstra%20Tutorial). [wordladder2.py](https://github.com/st0le/lost-in-compilation/blob/master/Dijkstra%20Tutorial/wordladder2.py) uses bidirectional search.