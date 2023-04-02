---
title: 'Searching Techniques - DFS - Tutorial'
date: 2013-05-21T23:28:00.000-07:00
draft: true
url: 
---

  
  

> Man - a being in search of meaning.  
> \- Plato

 A lot of Computer Science problems are simply search problems. Whether you're searching for an element in an array or searching for a solution to a travelling salesman problem, you essentially sift through a lot of possibilities and pick one.you determine as a solution.  
  
One of the most common search technique is called [Depth First Search](http://en.wikipedia.org/wiki/Depth-first_search), DFS for short. Now that's really just a fancy term for brute-force-with-backtracking. I'll be covering [Breadth First Search](http://en.wikipedia.org/wiki/Breadth-first_search) in another post. But the main difference between a DFS and BFS is that BFS doesn't backtrack. We'll discuss the differences in detail in the second post.  
  
In a DFS, we keep try to improve upon a mediocre sub-solution until we either find a solution or realize that it's not a solution at all, in which case we backtrack to a previous sub-solution and try something new.  
  
Things to remember when implementing a DFS.  
  

*   It's more efficient in terms of memory. (Compared to BFS.)
*   It'll find a "solution" faster.
*   The first solution it finds is not necessarily an optimal solution.
*   Needs a stack for the implementation. Ergo, can be implemented using recursive functions.
*   Need to keep track of previous sub-solutions, because the algorithm might find a cycle and flip between them infinitely.

There are many problems that are ideal for a DFS. A few classical examples include the [8 Queens Puzzle](http://en.wikipedia.org/wiki/Eight_queens_puzzle), Maze Solvers, etc To visualize a DFS, imagine that the problem is a graph with each vertex is a state of solution. Our goal is to find a path from the source-state to the final goal-state passing through these vertices.

  

DFS can be implemented as a recursive function or an iterative one. Here's the pseudo code for both. 

  

  

  

  

Note: The check for _already-visited_ is only needed if there is a possibility of encountering an already visited sub-solution during the search. Otherwise, it can be ignored. So watch out for that.