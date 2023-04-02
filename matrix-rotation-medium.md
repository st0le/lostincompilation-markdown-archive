---
title: 'Matrix Rotation - Medium'
date: 2013-06-07T17:26:00.001-07:00
draft: false
url: /2013/06/matrix-rotation-medium.html
tags: 
- computer science
- algorithm
- medium
- interview question
---

  

> Problem - Write an algorithm capable of rotating a matrix, in-place without any auxiliary storage.

  
I don't have an elaborate thought process to develop this algorithm. It's a few rules you ought to remember to implement rotations in the matrix.  
  
To implement these rules, you need some helper functions which are quite simple really. You need to be able to transpose a matrix, reverse a row, reverse a column. That's it. The rest is just a combination of these 3 functions.  
  
  

Python is awesome, isn't it?  
_Note : These functions create copies of the matrix, we can design algorithms that modify the original matrix with ease for square matrices. For non-square matrices, we have to create new matrices._  
  
Okay, let's get to the rotations. So we need to perform three kinds of rotations. 90,180,270.  
  
1) Rotation by 90/-270  degrees  
  

1.  Transpose the Matrix
2.  Reverse each row

  
2) Rotation by 180/-180 degrees  
  
There are two methods:  
  
First Method, is clearly obvious, perform 90 degree rotation twice.  
Second Method contains two steps, both these operations can be done in any order,  
  

1.  Reverse Each Row
2.  Reverse Each Column 

  
3) Rotation by 270/-90 degrees  
  

1.  Transpose the matrix
2.  Reverse each column

  
  

  
You can find the entire source code [here](https://github.com/st0le/lost-in-compilation/blob/master/matrix_rotation.py).