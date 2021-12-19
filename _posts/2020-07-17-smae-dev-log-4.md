---
layout: post
title: "SMAE Dev Log #4"
date: 2020-07-17 11:30:00 -0500
categories: Devlog Game SMAE
description: "Epic Save"
---

I grinded out a lot in a day, it's just that I also took a break and didn't update this blog. Anywho, two major
features added were lines and saving. The lines actually weren't too hard since a lot of the code was similar to
the vertex tool. I just had to keep track of which vertexes are being selecting when making a line, and use some
fancy math for selecting the line. Saving was also added and this took most of the time. I want to optimize it
however I can and also want to try out some stuff so I started using binary files. It's pretty cool.

I found [this guide](https://www.eecs.umich.edu/courses/eecs380/HANDOUTS/cppBinaryFileIO-2.html) which helped me
with doing this file IO. Basically you just have a save and load function in your class and that manages saving
and loading the data. I need to store two things for each map object type, the amount of that object and the data
itself. If I was using text then I could have an unlimited amount of objects because I could use markers to
determine where each data type section is, but the main thing is I don't need a human to be able to read the file
and numbers get some compression so binary is better. For the [raycaster](https://github.com/MisterMjirFunStuff/raycaster)
I made (editing the code from 3DSage's tutorial) I used text because I didn't bother with making a map editor, so I needed
the map to be human readable so I could edit it.

So just store how many vertexes there are and then store the vertex data, and repeat the process for the other map data
types.

I guess the roadmap for now is complete the game, clean up the code, and then optimize more, and possibly release it on
steam.

Here is a picture of what the editor looks like now:

![](https://mistermjir.github.io/assets/images/smae/smae_dev_log_4_1.png)

Now I gotta make sections and walls, after I finish those I can start working on the game engine.
