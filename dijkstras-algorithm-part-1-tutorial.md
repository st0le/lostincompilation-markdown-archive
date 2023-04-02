---
title: 'Dijkstra''s algorithm - Part 1 - Tutorial'
date: 2013-04-24T15:26:00.001-07:00
draft: false
url: /2013/04/dijkstras-algorithm-part-1-tutorial.html
tags: 
- tutorial
- computer science
- python
- algorithm
---

  
This will be a 3 Part series of posts where I will be implementing the Dijkstra's Shortest Path algorithm in Python. The three parts will be  
  
  
1) Representing the Graph  
2) Priority Queue  
3) The Algorithm  

  

To represent a graph we'll be using an [Adjacency List](http://en.wikipedia.org/wiki/Adjacency_list). Another alternative is using an Adjacency Matrix, but for a sparse graph an Adjacency List is more efficient.

  

### Adjacency List

An Adjacency List is usually represented as a HashTable (or an Array) where an entry at \`u\` contains a Linked List. The Linked List contains \`v\` and optionally another parameter \`w\`. Here \`u\` and \`v\` are node(or vertex) labels and \`w\` is the weight of the edge. By Traversing the linked list we obtain the immediate neighbours of \`u\`. Visually, it looks like this.  
  

[![](http://2.bp.blogspot.com/-aWqGEdAlM6I/UXhZOkb0epI/AAAAAAAABNA/i1U08S1Epb0/s1600/adjaceny-list.gif)](http://2.bp.blogspot.com/-aWqGEdAlM6I/UXhZOkb0epI/AAAAAAAABNA/i1U08S1Epb0/s1600/adjaceny-list.gif)

  

For implementing this in Python, we'll be using the [dict()](http://docs.python.org/2/tutorial/datastructures.html#dictionaries) for the main HashTable. For the Linked List we can use a list of 2 sized tuples (v,w). 

>   
> Sidenote: Instead of a list of tuples, you can use a dict(), with the key as \`v\` and value as weight (or a tuple of edge properties). The  Advantage being you can check for adjacency faster. In Dijkstra, we don't need that check, so I'll stick with a list for now.

So here's the python code  
  
The above program simply reads 3 integers per line from the data piped to it (or a file passed as an argument)  
  
I'll be using the undirected graph from Wikipedia for reference. Here's the graph followed by its textual representation.  
  

[![](http://2.bp.blogspot.com/-7V53zsSt1x4/UXhYAltxe8I/AAAAAAAABM0/em48f9Fs4PI/s320/g.png)](http://2.bp.blogspot.com/-7V53zsSt1x4/UXhYAltxe8I/AAAAAAAABM0/em48f9Fs4PI/s1600/g.png)

  
  
_(Sorry about the overlapping edge labels, I'm new to Graphviz.)_  

>   
> 1 2 7  
> 1 3 9  
> 1 6 14  
> 2 3 10  
> 2 4 15  
> 3 4 11  
> 3 6 2  
> 4 5 6  
> 5 6 9

  
So what have we accomplished so far? We essentially have stored the entire graph as a data structure, where we can iterate over the neighbours of any vertex using something like

That's it for this part. In the next part, we'll be building our very own Priority Queue with a little help from Python's Standard modules. Until next time...