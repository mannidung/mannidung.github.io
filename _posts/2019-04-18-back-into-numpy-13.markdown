---
title:  "Getting back into NumPy, Day 10"
date:   2019-04-18 21:49:09 +0200
categories:
  - Programming
tags:
  - NumPy
  - Python
---
I’m so ready to throw this problem away and start working on something else. Another day of debugging and finding the error, and right now I don’t know if the error is with me not remembering the algorithm properly, or that something is wrong with my operators.

Currently, the algorithm gets stuck after 1 iteration. It takes the start guess, applies the projection onto the first set, onto the second set, and then it doesn’t change. The error between the true image and my guess stays the same, and nothing seems to happen. I need to take a look in my collection of papers on this matter before this drives me crazy.

One other thing that makes me confused is that the phase of the FFTs are very blocky. I’m not sure where this comes from, and I don’t know how much this influences the result. It shouldn’t create too much trouble (I think), so I don’t know how important this is for the convergence.

Well, I’ve learned a lot, though, even if the progress was minimal. Fancy indexing is very logical, and I’m starting to get the hang of matrix handling in NumPy.

And to keep today’s post from being horribly boring, here’s a picture showing the current state of my program. I have to say, the guess seems to be closer than the guess I was able to produce yesterday… :-)

![Getting closer… or at least not further away. I hope…](/assets/blogpost_images/2019-04-18_01.png)