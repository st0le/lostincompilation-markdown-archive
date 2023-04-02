---
title: 'Word Ladders - Medium'
date: 2013-05-19T17:23:00.000-07:00
draft: false
url: /2013/05/word-ladders-medium.html
tags: 
- computer science
- algorithm
- medium
---

  

> [Word ladder](http://en.wikipedia.org/wiki/Word_ladder) is a word game invented by Lewis Carroll. A word ladder puzzle begins with two words, and to solve the puzzle one must find a chain of other words to link the two, in which two adjacent words (that is, words in successive steps) differ by one letter. Eg. SPORT <-> SHORT

_Source: Wikipedia_  
  
If you've followed my previous Dijkstra's Shortest Path Algorithm Tutorial, you'll be able to solve this challenge with minimum effort.  
  
Essentially, we create a graph where each word is a vertex and there exists an edge if two words differ by a single character. To find the word ladder is basically running any shortest path algorithm. You could also use a Breadth First Search.  
  
Some important observations  
  

*   The length of the _source_ and _destination_ words must be the same for a path to exist.
*   The path from _source_ to _destination_  can only contain words of the same length. So we can prune off the rest of the dictionary.
*   The graph is undirected.

Here's my implementation, it uses the modules from the tutorial.

  

  

  

To run the program, "wordladder.py SOURCE DESTINATION < dict.txt"  
For eg.  
  
```
C:\\>wordladder.py BOX TEN < words.txt
(4, \['BOX', 'BOD', 'BED', 'BEN', 'TEN'\])


```