---
title: 'Stack with Min() Operation - Easy'
date: 2013-04-28T12:36:00.002-07:00
draft: false
url: /2013/04/stack-with-min-operation-easy.html
tags: 
- computer science
- algorithm
- easy
- interview question
---

> Problem : Implement a stack with push() , pop() and a min() (which returns the minimum element in the stack). All operations should be O(1).

Another popular question, I've searched around a lot came across many answers, but only one had completeness. It's important to note that with the stack you don't have random access to the contents of the stack when implementing your solution.  
  
The solution I'm describing involves using 2 stacks, one is to store the data elements themselves (_mainstack_) and the other to store minimum values, which i'll refer to as _minstack._ Now we can have 2 parallel stacks where we push and pop on the minstack along with the mainstack, keeping track of the minimum value of course. But we can optimize this further. We only need to push values on the minimum stack only when you push a value on the main stack that is _less than or equal_ to the current top element of the minstack.  
Here's are the two stacks after pushing 67,44,20,77,99,12 in that order.  
  

[![](http://3.bp.blogspot.com/-6Pv3WdOmWIU/UX1xIB8bQQI/AAAAAAAABPA/ht2My9xCoq0/s320/push.png)](http://3.bp.blogspot.com/-6Pv3WdOmWIU/UX1xIB8bQQI/AAAAAAAABPA/ht2My9xCoq0/s1600/push.png)

  
  
When an element is poped, you check if the value on the minstack top is the same as the one on the mainstack, if it is we pop it from the minstack as well. Here's me poping 12.  
  

[![](http://4.bp.blogspot.com/-5XMk7-3Wo4A/UX1xJmvChzI/AAAAAAAABPI/3m9mQWgdl0I/s320/pop.png)](http://4.bp.blogspot.com/-5XMk7-3Wo4A/UX1xJmvChzI/AAAAAAAABPI/3m9mQWgdl0I/s1600/pop.png)

  

Let's get to the code now. I pick Java as my weapon of choice.  
  
Complete Code can be found [here](https://github.com/st0le/lost-in-compilation/blob/master/StackMinExample.java). It's important to note that we can implement both max() and min() for the same stack. You'll need one more stack for keeping track of the maximum element. I'll leave that as an exercise for you. Cheers!