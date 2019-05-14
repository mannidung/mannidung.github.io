---
title:  "Getting back into NumPy, Day 5"
date:   2019-04-08 21:49:09 +0200
categories:
  - Programming
tags:
  - NumPy
  - Python
---

A couple of days of travelling have messed up the schedule. I’m just going to continue on with my journey, even though the numbers are off :-)

Today’s post is a short one. I’m still preparing some small stuff before starting with the algorithm. I have to admit: I need to read up a bit on the details of the alternating projections. I don’t quite know how the projections are formulated, and until I have had time to do that, I’m going to prepare as much as I can.

Today’s code creates a random start guess. It’s nothing more than a matrix filled with normal distributed random numbers. This matrix is then element wise multiplied with the aperture matrix (the circle from Day 4, remember?).

The scattered image is then computed by taking the FFT of the random start guess and plotting its amplitude.

The code is short, but the images are beautiful! Enjoy!

![Element wise product of random start guess and aperture](/assets/blogpost_images/2019-04-08_randomguess_aperture.png)

![The scatter pattern of the random start guess. Isn’t it beautiful?](/assets/blogpost_images/2019-04-08_scatterpattern.png)


And the code that generated these pictures are:

{% highlight python %}
## Start guess
start_guess = np.multiply(np.random.randn(n, n), aperture)
## Start guess FFT
start_guess_fft = np.fft.fftshift(np.fft.fft2(start_guess))
{% endhighlight %}