---
layout: post
title: Cocos2D Python Ultimate Guide - Part 1
description: First part of the all-inclusive guide for the Cocos2D Python framework
---

Welcome to the Ultimate Cocos2D Python Guide! This is mainly a port of my [GitHub example repository](http://github.com/liamrahav/cocos2d-python-tutorials), with explanations and 
in depth blog posts! For this first post, I'll be copying the README here and giving the first example as a lesson. Enjoy!

<div class = "line line-full center" ></div>

 Cocos2D is a great platform for writing 2D interactive graphics programs in Python, but it can be tricky to get started. This tutorial is here to solve that! 
 The Cocos2D Python team describes it as "...a framework for building 2D games, demos, and other graphical/interactive applications."
 
 Feel free to read through the installation process, but if you already have it set up, you can just scroll down and jump straight into the first tutorial.

----------------------------------------------------------------------------

Cocos2D has a quite a few dependencies, and you need them all. To begin, make sure you have pip installed. 
You can check this by running `pip -V` in terminal. You should get a version name and a directory, such as 
`pip 6.1.1 from /usr/local/lib/python2.7/site-packages (python 2.7)`. 
If you don't have pip installed, check [this site]( https://pip.pypa.io/en/stable/installing.html) for instructions.

Once you have pip you will need to install the following dependencies. Only the first two are required, but the rest provide additional support (such as particles and audio) that may come in handy later: 

###Six
Six is a compatibility library that allows for code to be more easily transferable between python 2.x and 3.x

To install it, run either ```pip install six``` or `sudo pip install six` depending on whether you are using venv or not.

###Pyglet
Pyglet is a python library for writing graphics in python. Cocos2D is built on top of Pyglet (for the most part).

To install it, run either `pip install pyglet` or `sudo pip install pyglet` depending on whether you are using venv or not.

###NumPy
NumPy is a python package that deals with complex mathematics and scientific computing. You'll need this for particle support.

On Mac, installation is made easy thanks to Homebrew. If you don't currently have Homebrew installed, run 
`ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
 in terminal. Then you can simply run `brew install numpy` and `brew install scipy` to make sure you have the full SciPy package.

On other operating systems such as Windows or Linux distributions, head to [this site](http://www.scipy.org/install.html) for more information on how to install for your particular operating system.

###AVbin
AVbin is a package that provides some audio and the video support for Cocos2D Python.

Head to [this site](https://avbin.github.io/AVbin/Download.html) to download the correct installer for your operating system.

###SDL
SDL is the framework that PyGame (another Python game library) relies on for audio support. Cocos uses it for its audio as well.

Head over to [the first site](https://www.libsdl.org/download-1.2.php) to download the base SDL library and then to [this site](https://www.libsdl.org/projects/SDL_mixer/release-1.2.html)
 to download the Mixer library from SDL (which was what we will be using for audio support in our games)

----------------------------------------------------------------------------
Now that you're all set up you should be ready to install Cocos2D

###Cocos2D
This is the most essential library for these tutorials and examples. It's pretty similar to install like everything else here.

Simply head to your terminal and type in `pip install cocos` or `sudo pip install cocos` depending on whether you are using venv.

----------------------------------------------------------------------------

### Tutorial Structure

If you're following along on the [GitHub repository](http://github.com/liamrahav/cocos2d-python-tutorials), you'll probably want to read this section of the post.
The code is grouped in folders by their difficulty level. Here is how it's mostly layed out:

     root directory/                    
         |                              
         | readme                       
         | --> difficulty/              
             |                          
             | --> assets/              
             | readme                   
             | examples                 


From here you should be ready to start reading through the samples and trying out the concepts yourself. I group the the code by difficulty level, so I recommend starting in the `basics` folder and working your way up.

It's important to note that `basics` does not mean Python basics! You should at least have a basic grasp on writing object oriented code before trying to jump into Cocos2D Python!

*I highly recommend that you browse through the code and READMEs on GitHub, and only use the cloned repository to run the games*

-------------------------------------------------------------

Cocos has also provided some pretty good basic documentation and video samples, but unfortunately it stops there. You can check those out [here](http://python.cocos2d.org/doc/programming_guide/index.html)


I created this guide because I found the Cocos2D Python documentation to be extremely limited, especially in code samples, beyond the basic level. It is also relatively complex and hard to understand. I often found myself needing to look at the source code for explanations on how to use certain classes and features. 

If I had tried to teach myself Cocos half a year ago, when I was just getting familiar with intermediate concepts in Python and object oriented programming itself,
 I would have been hopelessly confused. These guides are aimed towards people in that level.

-------------------------------------------------------------

Alright! Now that you're all set up we can jump straight into some code. I'm going to go ahead and assume that you have not only basic knowledge of Python,
but also some experience with object oriented code.

So, now that we're ready to begin, we need to make sure everything is set up. I personally use PyCharm as my Python IDE of choice, so I'll using that as my guide when
it comes to project settings. Most people typically have more than one version of Python set up, those usually being some flavour of Python 3.x.x and Python 2.x.x. You're
going to want to make sure you're running on a Python 2.x.x version of Python, and you're going to want to make sure that version of Python has all the required libraries
stated above.

Let's hop into some code. I personally called this file `start.py` but you can call it whatever you feel is appropriate.
First, like with many Python programs, we want to import some Python files to provide the base functionality for us to build upon. Let's start
by importing these files:
    
     import cocos                            
     from cocos.text import Label            
     from cocos.scene import Scene           
     from cocos.layer import Layer           
     from cocos.director import director     

Really you could get by just from importing the base cocos package, but importing all of these files saves us from chaining together huge names to get commonly used
classes.

The first thing we're going to need to do to kick off a Cocos2D Python program is make a Layer. Layers are exactly what they sound like: They are layers within the scene created
by Cocos. For example, in the opening menu of a game, you might have a Layer for the actual menu, a Layer for the music, and a Layer for some animations in the background.

The custom Layers that you make will be extensions of the `cocos.layer.Layer` class. It'll need to have an `__init__` function that gets called when the object is created.
In that function, we will want to call our custom Layer's super class (in this case `cocos.layer.Layer`) so it can do everything it needs to make a Layer. Here is the code for this:

     class HelloWorld(Layer):                              
        def __init__(self):                                
            super(HelloWorld, self).__init__()             
            
Nice! Let's make this Layer just display a Label with some text in it for our first Cocos2D Python program. We can simply make a variable with a `cocos.text.Label` object
stored within. I'll be passing in some relatively self explanatory parameters, except for the `anchor_x` and `anchor_y` values, which simply tell Cocos2D Python where I want
to stick the text to.

     hello_world_label = Label(                            
                 "Hello World!",                           
                 font_name = "Times New Roman",            
                 font_size = 32,                           
                 anchor_x = 'center',                      
                 anchor_y = 'center'                       
             )                                             
             
That was surprisingly simple! Cocos2D Python is especially great for expected tasks such as text, menus, and many other common game interfaces.

Next we can just set the position of the Label on the screen by adding this little line of code:

     hello_world_label.position = 320, 240 
     
And, of course, we need to actually add this Label to the layer, or else nothing would actually happen when we ran the Python file.

     self.add(hello_world_label) 
     
Awesome! So now we have a full custom Layer called HelloWorld that looks something like this:

     class HelloWorld(Layer):                              
         def __init__(self):                               
             super(HelloWorld, self).__init__()            
             hello_world_label = Label(                    
                 "Hello World!",                           
                 font_name = "Times New Roman",            
                 font_size = 32,                           
                 anchor_x = 'center',                      
                 anchor_y = 'center'                       
             )                                             
             hello_world_label.position = 320, 240         
             self.add(hello_world_label)                   
             
The last part we need is something that we generally see across all Cocos2D Python programs. Cocos runs by creating a director object which "directs" the scene object. The
scene object contains all of the layers and the position and order that you want in the end result.

The first thing you need to do is initialize the director. This is done with a very simple line of code:

     director.init() 
     
That line of code sets up the things in the background that we need in order to actually make a window appear from our Python code. Forgetting that line in any Cocos2D Python
program will give you a bunch of errors.

Now we want to run the scene. This can be done by creating a scene object, and then running it. However, I prefer to simply chain it all together into one bigger line that
looks like this:

     director.run(Scene(HelloWorld()))
     
And that's it! Give it a run and it should work! If you haven't typed out the code feel free to grab it from my [example on GitHub](https://github.com/LiamRahav/cocos2d-python-tutorials/blob/master/basics/start.py)
If anything described above does not make sense, try implementing it yourself or checking the sample on my GitHub, where I've written extremely detailed comments about every
line of code.

Until next time! Feel free to leave any comments down below.

