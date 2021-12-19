---
layout: post
title: "SMAE Dev Log #3"
date: 2020-07-11 22:01:00 -0500
categories: Devlog Game SMAE
description: "Big features, very cool"
---

I made a lot of progress this time around. So first I was looking around at other mad editors and 3DSage's map editor for a
DOOM style engine and I decided I needed to change up the colors to look cooler. That's not a big thing though, I finally
can add points through the user interface. Not only can I add points, but now I can delete them. What did it cost? A bunch
of time, poorly written code, and the zoom feature (rip zoom, it doesn't zoom into the center anymore)

So first I did the color changing, not too hard. I thought. Somehow I was getting float point exceptions even when I used
```glColor3ub``` but anywho, eventually it decided to work. Also, I did a lot of fancy event handling and now the window
buttons are pretty much deprecated now that you can use the mouse to control. It's so much easier to move the screen
and zoom in and out with the mouse.

<img src="https://mistermjir.github.io/assets/images/smae/smae_dev_log_3_1.gif">

Next I started working on adding the tools. You can already see the button in the image above but as it is there it's just
a visual thing. I created a toolmanager which does most of the heavy lifting for the tools and got it to select and deselect
a tool. This would make the box turn a cool blue color. However, I decided to go even further with this. I actually started
implemented how the tool would work. Similar to the map data, each tool has a type, and based on the type of the tool that's
selected different stuff happens. First I added a visual hover thing so you can see where your point will snap to when you
select the vertex tool and hover your mouse. This was pretty easy. Get the mouse position and grid size, figure out if the
mouse's offset from the grid line is greater or less than half the grid size, and then either subtract the offset or add
the grid size minus the offset. Works on both directions. This was getting even cooler, but we're still not stopping. Next,
I made it so you can add a point to the map. It was at this point I removed the view offset, because I could place the point
pretty easily, but it wasn't showing up in the right place. Removing the view offset made that easier to deal with but the
problem is now the zoom doesn't zoom in towards the center of the screen. I'm actually not gonna deal with problem for now.
Finally, here is what the progress looks like.

<img src="https://mistermjir.github.io/assets/images/smae/smae_dev_log_3_2.gif">

This next step took a lot of processing power (from my brain, rips). I want a vertex to glow if you are 'selecting' it. This
is where the bad code comes in. So I added a property for the vertex to tell if it's selected, but to check if something is
selected you have to loop through all the map data, check if the data is a vertex, and then check if that vertex is selected.
Not too hot. However, now that I have a way to check if something is selected, I can now easily delete points.

Keep in mind when I say 'easily', it may not always be as 'easy' as it sounds. I usually spend a lot of time thinking about the
solution and there is plenty of room for improvement. If you are trying to develop an engine / map editor like this and are
frustrated by how 'easy' it is, just know it's not easy and pretty hard. But with more experience I can guarantee it will get
easier to do.

I also don't want to talk too much about specific implementation details because I am doing this project as a copy the end result,
not the process. If that were the case I would be looking through DOOM's source code (and the linux version is in C, a language
I kinda know but not really). If you want to make your own engine / map editor, try to copy my results with your own implementation,
get creative!

Anywho, here it is:

<img src="https://mistermjir.github.io/assets/images/smae/smae_dev_log_3_3.gif">

Now there are some changes under the hood. I've added a bunch more map data stuff, but also I wanted the tools to display their own
names so it would be easier for anyone (but most important me, who will probably forget what each button does) to figure out the UI.
I implemented this but was struggling to figure out why this wasn't working. First dumb mistake was I tried to initialize the
textures before OpenGL was ready, and this is one of the things you have to be careful about when using OOP. Fortunately, that was
as easy to fix as simply moving the initializing of the tool manager after I initialized GLEW. I was using SDL_ttf to get some fancy
fonts but it just wasn't working! To my luck I found [a very helpful article](https://moddb.fandom.com/wiki/SDL_ttf:Tutorials:Fonts_in_OpenGL) which lead me to success.

Now I got this:

<img src="https://mistermjir.github.io/assets/images/smae/smae_dev_log_3_4.gif">

First I was going off just reading on [DOOM WADs in the DOOM Wikia](https://doom.fandom.com/wiki/WAD) but now I have increased my
resources and am also referencing 3DSage's DOOM like engine because it's a really nice looking editor.

I'm still experimenting between the correct amount of detail and results to put on this blog. I think talking more about the process
would be interesting but I also want a general person to be interested in this and understand it in layman's terms. I'll eventually
release the source when I finish and make a Wiki so you can see all the implementation you want, but basically I am still looking
for the sweet balance for this blog. I also want this to be a fun place for me to reference what I was thinking when making the game
and a progress tracker as well. I hope (when I finish this) other people can see how you slowly build features one by one and
eventually you too can make something cool.
