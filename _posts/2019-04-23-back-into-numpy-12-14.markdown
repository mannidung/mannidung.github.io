---
title:  "Getting back into NumPy, Day 12, 13, 14"
date:   2019-04-23 21:49:09 +0200
categories:
  - Programming
tags:
  - NumPy
  - Python
---
These last few days I’ve spent trying to learn Electron. “Electron!?”, you think. “But that’s not Python!”. And you are right. Electron is he JavaScript-Chromium-HTML-thing that helps you make nice GUIs and fancy apps using web technology.

## In need of a GUI
So why am I looking into that? Well, I’ve decided to get back to what I started on at day 1: the keystroke analyzer. And I want to make a fancy GUI for it. And since I haven’t found a nice GUI toolkit for Python, I decided to take the hard way.

A little bit of googling led me to a blog post telling big brave stories of how software developers were able to couple Node.js with Python using a tool called zerorpc. This allows you to run a Python service as a server, and Node.js as a client, and you can exchange data between them without having to deal with manually creating sockets.

Turns out it isn’t as easy as I thought it was (maybe you start to see a pattern here…).

## The three steps
First I had to get to know Electron. That was quite easy. Half a day or so and I was able to create an app and understand roughly how it works. That’s all you need to get started, the rest you can learn as you go along.

The second step was to understand how zerorpc works when you want to connect node.js with Python. This wasn’t as hard either, since zerorpc has great examples on their website.

The third step was to get to work. Or… more correctly, the third step is to get it to work. It’s not working yet, but I think I’m getting closer. I’m going to post a how-to on how to set up the environment when I’m done, and the following paragraph will serve as a reminder for me to describe the most important step.

## Compilation time!
Compilation? What? Isn’t that the whole reason why we choose Python and JavaScript? To avoid compiler errors and instead have the application blow up in our faces when we execute it, instead of when we try to build it? Well, yes, it is.

But in order to set up the environment I had to compile ZeroMQ, the engine behind zerorpc. This compilation was executed by Node.js, and, apparently, Node.js needs Python2 to be able to compile. And I had a Python3 virtual environment.

So… first it took some time before I figured out what was wrong (note to self: read the error messages more thoroughly next time). After that it was easy. Remove the symlink called python, replace it with a new one linking to the python2.7 installation available on your system (if you don’t have python 2.7 installed, create another virtual environment with python2.7 and link to that). Run the npm install command, wait for the compilation to finish, and replace the python2.7 symlink with python3 again.

Situation update: some errors are still there…
And where do we stand right now? Well, at this error message…

![Appearently I compiled against the wrong Node version or something…](/assets/blogpost_images/2019-04-18_01.png)

As I understand it, I compiled against the wrong Node version.

If you need me, I’ll be crying in my closet.