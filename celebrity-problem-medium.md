---
title: 'Celebrity Problem - Medium'
date: 2013-06-19T17:33:00.001-07:00
draft: false
url: /2013/06/celebrity-problem-medium.html
tags: 
- computer science
- algorithm
- medium
- interview question
---

  

> Problem : In a party of N people, only one person is known to everyone. Such a person may be present in the party, if yes, (s)he doesn't know anyone in the party. We can only ask questions like “does A know B? Find the celebrity in minimum number of questions.

  
This is a very interesting problem. The answer, ie the least number of questions required, changes based on what's given. Are we guaranteed there's one celebrity in the party? Does every non-celeb know every other non-celeb? ( not very ideal, but under a best case scenario. )  
  
Once again, the rules  

*   There is at most one celebrity at the party
*   Everyone knows the celebrity.
*   The celebrity knows no one.
*   We can only ask the question "Does A know B?"

  
When we ask the question, we can get a "yes" or "no". Each conveying information about both the participants in the question. Let's see those outcomes...  
  
If the Answer is "Yes", we know A is definitely not a celebrity. But B is a candidate for a celebrity.  
  
If the Answer is "No", we know both A and B are both candidates or both are Non-Celebrities.  
  
Turns out, we can do this in linear time. We love those kinds, don't we?  
  
Here we simply assume the first guy is a celeb. Each time you will ask a question  

> Does my _assumed-celeb_ know the _current__\-guy ?_

 There are two outcomes,  
  

*   If the answer is "Yes", we know our assumption was wrong,we can eliminate our assumption. But the next-guy could be a celeb. So we make him our new assumption.
*   If the answer is "No", our assumption is holding strong, we can safely eliminate the _current-guy._

  
Evidently, every time you ask the question, one guy gets eliminated from candidacy. So we'll need to ask (n - 1) questions to get one strong candidate.  
  
At this point, _**if**_ we were assured there was one celeb we can end the algorithm here. If there's a possibility, there was no celebrity, we'll have to perform one more scan to eliminate the end guy as well.  
  
Theoretically, that's (n - 1) questions. So we need to ask a minimum of 2(n-1) questions to figure out the celebrity. I'll attempt to prove the lower bound some other time, will be handy for my Algorithm class.  
  
  

Let's extend this a bit, assume there were multiple celebrities at the party (or None). (A celeb doesn't know another celeb.) Although, I don't claim this is the most efficient algorithm, it certainly works. The first part of the solution remains the same, we find a celebrity, any one will do. Notice the original algorithm will do this for you. We include one more pass at the end, asking the question _"Does X know Celebrity?"_. If the answer is "No", we KNOW that X is another celebrity. Here's the code.  
  
Lovely question, Thanks to [CodeBunk](https://www.facebook.com/codebnk) for posting it.