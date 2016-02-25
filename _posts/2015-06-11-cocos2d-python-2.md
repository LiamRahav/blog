---
layout: post
title: Cocos2D Python Ultimate Guide - Part 2
description: Second part of the Cocos2D Python guide, where we will cover sprites 
---

Welcome to the second part of this guide! If you're just joining in, I would check the [first post]({{site.baseurl}}/2015/06/05/cocos2d-python-1/) and would open
the [GitHub repository](http://github.com/liamrahav/cocos2d-python-tutorials) in a new tab or have it cloned on your machine.

Today we'll be checking out how to do a pretty basic but extremely important thing in Cocos2D: Sprites. For those who don't know sprites are "a computer graphic that
 may be moved on-screen and otherwise manipulated as a single entity" (Google). 
In this case, a sprite is simply an image that we can load and manipulate. For this particular sprite, I'll be using the Cocos2D Python mascot,
[Grossini](http://liamrahav.me/files/grossini.png).

![Picture of Grossini](http://liamrahav.me/files/grossini.png)

We can begin by making a python file (in this case I named it `actors.py`) and then importing Cocos and the commonly used Cocos classes:

	 import cocos                                
	 from cocos.text import Label                
	 from cocos.scene import Scene               
	 from cocos.layer import Layer               
	 from cocos.director import director         
	 from cocos.sprite import Sprite             
	
Now we will do just as we did last time and make a custom layer out of a class that extend's Cocos's `cocos.layer.Layer` class. This time, however, we will be 
adding a sprite instead of text. So, to begin, we simply make a class that extends Layer and calls the Layer superclass:

	 class Actors(Layer):                             
	     def __init__(self):                          
	         super(Actors, self).__init__()           
			 
Now is where the code starts to change from the last tutorial. We will make an object variable that holds the sprite, unlike last time in which we made a local variable.
In fact, it's always a good practice to use object variables simply because they will be editable from any function within or even without the class.

To declare a `cocos.sprite.Sprite` object, this is all the code you need:

	 self.actor = Sprite('grossini.png') 
	
Awesome! We now have a sprite stored in our object. That's great, but how do we actually do stuff with it? For starters we're going to have to give the sprite a position
on the screen. Then we'll need to actually add it to the layer so that it shows up in our screen.

	 self.actor.position = 320, 240         
	 self.add(self.actor)                   
	 
Now simply comes the same director code as last time to initialize the director and then add our custom layer to the director's stack. Here's what the code for that
would look like:

	 director.init()                   
	 director.run(Scene(Actors()))     
	 
And that's it! Run the code and it should simply load the image and display it in the middle of the screen. Feel free to toy with the code, add text, change the image, 
etc. to get a better grip on how Cocos2D's Sprite system works. Here's what the full program should look like: 

	 import cocos                                                      
	 from cocos.text import Label                                      
	 from cocos import scene                                           
	 from cocos.layer import Layer                                     
	 from cocos.director import director                               
	 from cocos.sprite import Sprite                                   
 	                                                           
	 class Actors(Layer):                                              
	     def __init__(self):                                           
	         super(Actors, self).__init__()                            
	         self.actor = Sprite('grossini.png')                       
	         self.actor.position = 320, 240                            
	         self.add(self.actor)                                      
 	                                                           
	 director.init()                                                   
	 director.run(scene.Scene(Actors()))                               
	 
Until next time! Feel free to leave any comments down below.