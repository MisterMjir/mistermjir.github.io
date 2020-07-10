---
layout: post
title:  "SMAE Dev Log #1"
date:   2020-07-08 22:32:00 -0500
categories: Devlog Game SMAE
description: "Going to make an epic game"
---

I am beginning work on an epic game code named SMAE (it's just the initials of the full title!)
I want it to be like DOOM, and I may reference some techniques DOOM uses, but I want this project
to be one of those exercises where you look at a result and implement your own method to copy that
result. I don't want to spend too much time talking about the game, that's a surprise for when it's
finished, just know that this is gonna be epic.

I like old school game developers. Those people are absolute legends. They were masters of coding and
math, I wish I could've been in those days because it's harder to flex your skills when you have these
higher level languages which are taught and they make a lot of things easier. Anyways, I also have
plenty fun coding games from scratch (with code, not the website but the website's fun too!). For
our TSA Video Game Competition I coded the entire thing because I knew it would be fun rather than using
a game engine (which we were absolutely advised to use, had to convince advisor I knew what I was doing).
Despite all of that I think this is the fourth game I am making with C++. I tried to remake two of my
scratch games, one I just stopped working on it and the other never got to a playable point and the TSA
game is the third one.

Anywho, let's start with libraries. I am going to be using SDL2 with a combo of OpenGL. I could use
GLEW or something and get another sound library but SDL has an easy sound library extension and I've
tried it out and it works.

The first thing I need to do is figure out the map system. I'm just gonna heavily go off DOOM for this. So
the basic building block of the maps are vertexes (or points) and then there are other stuff like lines, walls,
sectors, enemies, ton of stuff. I'm gonna start of small and just focus on the vertexes, lines (for walls), and
a floor for my first goal. Making a map is gonna be kinda complicated so why not make a map editor?!

It was time to begin structuring my project, it is going somewhat like this:
```
game
map_editor
| - src
| - | - code goes here
| - CMakeLists.txt
| - README.md
CMakeLists.txt
README.md
```

Going to use CMake to build because that's the easy way I know to also get it working on Windows. I'm making this on
Ubuntu by the way because I don't want to do C++ in Windows.

So it starts with just a window. Then you gotta change the screen color to make sure it's actually working, and then you're
good to go! So I made the top part of the window just a standard grid you see sometimes and left some room at the bottom
for eventual tools I'm going to use.

If you really want to see some code then just wait for me to make some more progress, I will just upload it to GitHub so
you can see all of it.

The grid is looking epic, now let's add a player. This will just be the spawn point of the player at (0, 0), but that puts
it at the top left (remember how computer graphics work) so I'll add an offset so we can "center" the player on the screen.
I have activated glOrtho so we can use the computer graphics we are taught in school rather than the OpenGL projections
an transformations.

This is starting to get somewhere, now I want to move and zoom. Added a class to handle window buttons and boom! Now we
can move, zoom in, and zoom out! It looks like this:

<img src="https://mistermjir.github.io/assets/images/smae_dev_log_1.gif">

That's pretty much it for this log. The next step to reach the first goal is to add tools so we can add vertexes and line
(and possible a floor while we are at it). Then we gotta save this data into a file and then create a game to see if the
map works. Lot of stuff but slowly I can get there.

I think next time I should take more pictures of progress as I work through it so this blog can be a little bit better. One
GIF ain't gonna cut it if I don't want to bore you with the details of the code.

Hope you get inspired to do/make something fun.
