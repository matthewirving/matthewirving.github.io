---
layout: post
title:  Baby Steps
date: 	2020-11-09 15:34:00 -0300
image:	/assets/images/blog/post-2-error.jpg
author: Matt
tags: Personal, Web Development, Software Development, Errors
---


Hello and welcome back! I've been lacking in the last week or so with making progress with this blog, website, my projects, etc. But we're back now with some brand new things to talk about. Since my last post I have been working on my Bathroom Buddy project lightly. I opened a new branch called [wifi-tests](https://github.com/matthewirving/BathroomBuddyFinal/tree/wifi_tests) where I've been experimenting with XMLHTTP for the local website for my project. It was pretty simple to understand, my current implementation is actually based off of an example I had found online.

From my understanding all that's really happening in my program is that It's waiting for website calls for the functions "readTime" and "readName" that I wrote. readTime of course handles the display of the time on the website and is at least technically synchronized with the Bathroom Buddy's clock, but I'll get more into this later. readName handles checking who's in the bathroom and then passing that name to the website. For a first iteration of the website I think it's alright as it suffers from a couple of problems.

One of the biggest problems is that the connection from the ESP32 and my computer is causing a lot of requests to drop and fail even though my laptop is 6 inches away from it. I don't know if it's because of inefficient code or a bad connection, all I know is that my website spits "Err Not Connected" like no tomorrow. It also seems that it has a hard time updating the time and name at the same time and it appears that it can't. I have a couple ideas to make it more efficient though.

Right now my website uses a "setInterval()" function from JS to request the time from the ESP32 every second. Even a second grader could probably tell you this isn't ideal. So I think the plan for that is im just going to pass a boolean to the website and have "true" activate the timer and "false" just resets the timer and keeps it at zero. For the name handling I'm currently using the same "setInterval()" from the time handler and instead of every second, every five seconds the website asks the ESP32 for the name of the person in the bathroom. I'll definitely be changing this to just pass an integer to the website and store an array of everyone's names and have the integer just select the name. 

The most ideal solution would probably to find something else that doesn't rely on the website making the calls to the ESP32 for data updates in my opinion. I think it could be much more efficient if the website acted as the listener and passively accepted data. As opposed to the website having to actively ping the ESP32 for data and then having it sent back which just gives it a bigger opportunity for data requests or data to drop. Because of that I'm strongly considering either using a different method or figuring out how to do it with XMLHTTP. 

That's all for now, seeya next time.
-Matt