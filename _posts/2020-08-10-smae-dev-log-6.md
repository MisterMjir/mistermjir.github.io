---
layout: post
title: "SMAE Dev Log #6"
date: 2020-08-10 11:12:00 -0500
categories: Devlog Game SMAE
description: "Map editor done, but not really"
---

Took another long break from this, stuff is starting to happen but I am determined to make progress on this even if it's slow
progress. So first I finished up the map editor (the wall hovering is still messed up) and I included all the basic stuff I need.
I also started finally working on the game engine itself. There is still a long way to go, and this is definitely going to take
even longer if I don't work on it daily (which I won't be able to do). Now there are sections and floor heights and wall heights.
After I can render in a simple box (made in the map editor) then I will have to go back into the map editor and add stuff like
textures and cut-scenes and the like.

Now with proper OOP adding subtools is not too bad and the process is pretty straight forward. Each tool's functionality is
pretty self-contained so once I finish it up and release the source if someone is interested they could probably improve the code
a lot (although I should probably do that before another person looks at the code...). There are wall sub tools and section tools,
which are all the basic things I need to start working on the engine. Here are some pictures.

![](https://mistermjir.github.io/assets/images/smae/smae_dev_log_6_1.png)

![](https://mistermjir.github.io/assets/images/smae/smae_dev_log_6_2.png)

I guess most of the time was time spent (re)learning OpenGL. Every single time I need to go back to [Learn OpenGL](https://learnopengl.com) and review how to make a triangle. It's pretty challenging to remember how everything works without constantly
doing OpenGL stuff. A lot of time was spent making the engine and it took a while to see actual results but I worked step by step.

First I got a window working, copying most of the code from the map editor. Then I tried to draw a triangle, found some errors,
understood how it actually works, and got the triangle. Then I made it 3D for fun. For extra fun I made a pyramid.

![](https://mistermjir.github.io/assets/images/smae/smae_dev_log_6_3.gif)

I did get the loading stuff to work properly but putting that on the screen requires a bit more finesse so that's what I'm going to
work on next. Have the big picture in mind when working on a big project like this and make one small goal. Finish that small goal
and make a new small goal. Keep on doing that and eventually you'll finish (it will take perseverance but you, and more importantly,
  I, can make it through)
