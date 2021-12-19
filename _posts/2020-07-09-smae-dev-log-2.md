---
layout: post
title: "SMAE Dev Log #2"
date: 2020-07-09 23:02:00 -0500
categories: Devlog Game SMAE
description: "Remembering my C++ skills"
---

Another day another grind, unfortunately not much progress was made today. I was planning on getting vertexes
and lines done but I only kinda got vertexes working. The main problem I faced was class design (spooky).

So in my 'main' class of the application (which is the window), I needed a variable to store all the map data.
Now I don't want to have different variables for each type of map data, that's gonna become a big mess real
fast so I need to use base classes and subclasses, actually an abstract class and subclasses. I actually
thought of a pretty neat system, this is what the code is looking like for the MapData class and the vertex
class.

```c++
enum class MapDataType {VERTEX, LINE};

class MapData
{
public:
  MapDataType getType() {return type;}
  virtual ~MapData();
protected:
  MapData(MapDataType);
  MapDataType type;
};

class MapDataVertex : public MapData
{
public:
  MapDataVertex(int x, int y);
  int getX() {return x;}
  int getY() {return y;}
private:
  int x, y;
};
```

The line class will look something like this but instead of an x and y it will have two pointers to two points. One
tedious thing to implement will be deleting points, because I will have to iterate through all the lines to make
sure there is no line using that point. Of course I could use smart pointers but this will not work when reading
the data from text, as the vertexes will just have two ints for x and y.

Another challenge I am foreseeing is how to translate the pointers from code into text.

So about the code the thing I think is cool is the ```MapData``` constructor is protected, meaning we can guarntee
the type of the ```MapData``` object is correct. This is done in the constructor of the base classes, see below
for the implementation of ```MapDataVertex```'s constructor:

```c++
MapData::MapData(MapDataType type)
{
  this->type = type;
}

MapDataVertex::MapDataVertex(int x, int y) : MapData(MapDataType::VERTEX)
{
  this->x = x;
  this->y = y;
}
```

This way the types are guaranteed to be correct.

Then I just added a ```std::vector<MapData>``` data member to my ```Window``` class (which is like the main class)
and pushed some objects back during the initializing of the window. The big big big problem I had was remembering
how to do polymorphism in C++ after taking a course in C# (and making an app in it! (WIP)). So first of all the base
class needs to have a virtual method, and I forgot that (pre C# me definetely disappointed). So I just slapped
virtual onto the destructor and it should be ```virtual``` anyways in shenanigans like this. Now using objects and
downcasting gets really funky. I don't exactly remember the reason why but using straight up objects won't work,
you need to use pointers or references. This is because an object physically holds that data, so you would get some
mad object slicing. Pointers can make things a little bit easier because you are just referring
to the data and just telling how it should be interpreted. Anywho, before learning C# this would've been a no-brainer,
but C# makes this a tad easier to deal with so I had to dig deep into my memories to recall this information. Luckilly,
I think I am back so I am able to continue.

At this point ```std::vector<MapData>``` is now ```std::vector<MapData*>```.

VERY IMPORTANT. I looped through the vector and deleted all the objects in the ```Window```'s ```close``` function, for
every ```new``` there must be a ```delete```. So after some time spent trying to figure out something really simple I
finally got it working without a segmentation fault (don't worry if you don't know what it is, if you know, you know).
Unfortunately, I didn't get enough time to add a UI to add the points, but here is the result anyways:

<img src="https://mistermjir.github.io/assets/images/smae/smae_dev_log_2_1.png">

The UI for adding it is gonna be a little bit tricky. First I need to do something like the window buttons (the move and zoom)
so it will be easy to add new tools. Then I'm gonna have to do some 'snapping' with the mouse, meaning snapping the points
to the nearest grid spot while the mouse is hovering, adding the point when clicked, and also deleting the point when clicked.

Slowly but surely I will be able to put the player in a box and I can start working on the engine.
