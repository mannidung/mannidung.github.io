---
title:  "Getting back into NumPy, Day 11"
date:   2019-04-19 21:49:09 +0200
---
It’s time to give the alternating projections problem a rest. I’m on my 6th day or so debugging and error searching, and can’t get it to work. I have even compared it to my old code that I wrote during the course. And it worked back then. I MATLAB, not Python, but it worked.

I’ve written the algorithm more or less the same now as then. That’s why I’ve come to the conclusion that it is something going on in the background, some aspect of NumPy that I don’t understand yet. I have two suspects: the FFT operator or the way NumPy handles matrixes by reference and/or value.

My bet is on the FFT operator. The phase of the FFTd image is a bit strange, still. It’s blocky and doesn’t make sense to me.

The third option is that there’s something small that I’m too blind to see. It wouldn’t be the first time it happens, and a short time out from the code has helped before.

So, time to think of a new problem to solve… I have some ideas, let’s see what I start with tomorrow.

Anyhow, this banging my head against the wall has provided some nice statistics to my keystroke analysis project. So just to keep the streak with post with images going: here’s a heat map of my keystroke counting so far (for non-work time). Apparently I’m good at getting in bed in time!

![My keystroke heatmap for the last 30 days!](/assets/blogpost_images/2019-04-19_01.png)