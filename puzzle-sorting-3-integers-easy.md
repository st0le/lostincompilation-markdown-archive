---
title: 'Puzzle : Sorting 3 Integers - Easy'
date: 2013-04-12T01:18:00.001-07:00
draft: false
url: /2013/04/puzzle-sorting-3-integers.html
tags: 
- computer science
- algorithm
- easy
- interview question
---

This is a pretty silly question I came up with.  
  

> Problem : You are given 3 integers a,b,c. You are given 2 functions, "int max(int,int)" and "void print(int)". Using these 2 function and these only, print the numbers in increasing order. You're allowed to use math operators, but NOT programming language constructs like "if", "for", "while", including the ternary operation etc

  
So here's the solution. Again, beware of integer overflows.  

  
The idea here is if we negate the number, we can use the max() function to find the minimum number! Nifty eh?  
  
We don't need to use the auxiliary variables, those were added for clarity. Do you have an alternate solution? I'd love to see it. Leave a Comment.