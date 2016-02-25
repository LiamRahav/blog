---
layout: post
title: Hello, World
description: A brief introduction and a discussion about the "hello world" program
---

Hello, and welcome to my blog! For the most part I will be putting up small discussions on programming topics and perhaps short tutorials or updates on things I'm doing.
You can expect to see some other subjects popping up here and there, simply based on whatever I feel like getting out.

I'm just a high school freshman, and so chances are that you might not agree with everything I say (probably because a lot of it will be incorrect), so please feel free to leave 
comments in section below each post!


<div class="line line-full center"></div>


In the spirit of this "Hello, World" post, I want to quickly cover the topic of the "Hello, World" program. The more my skills have grown in regards to code, and the more I see
beginners around me hopelessly confused (especially in school), the more I realize the importance of the first program a programmer writes.

I've seen a lot of discussion on forums such as the [/r/programming](http://reddit.com/r/programming) subreddit regarding whether having first-time programmers print out 
"Hello, World!" is really the best first thing to do.

Some people complain that it's not appropriate because in many languages, take Java for an example, strings are not basic data types like numbers, and can bring very complicated
concepts to the table on day 1.

Others complain that it's just too simple. A boring program that just prints a meaningless sentence to the console can really discourage newbies. How long would it take them to actually 
make something useable? They make the arguement that a first time programmer should write something in a visual language like MIT Scratch or have someone guide them through JOptionPane-like 
GUIs to really get them excited  before they start with the basics.

While I tend to agree with the second point, I make a different arguement. I don't really think that it matters whether a first-timer prints "Hello, World!" or adds 3 and 4 together and 
prints it, or even makes a small GUI that can ask for someone's name and then present that information back. What really matters for a first-timer's first program is the language it's
written in.

Take a look at this basic Java "Hello, World" program:

     public class HelloWorld {                         
	   public static void main(String[] args) {        
	     System.out.println("Hello, World!");          
	   }                                               
	  }                                                
                             
Slow down! We have just shown our budding programmer *way* too many topics in one go. We have classes, visibility, functions, return types, static/final, arrays, parameters, and more
in what was supposed to be the most basic program they will ever write.

Now take this basic Python "Hello, World" program:

     print "Hello, World!" 
     
Huh, seems easy enough. Looks like we just tell the program to print whatever we put in the quotes. No questions like *"Why do you need semicolons after every line?"* or 
*"Why do you need this main thing to get the code to work?"*.

My dad came to me around a week ago, and asked me to teach him some code. He works in the financial sector, but most of his dealings are with tech companies. And so, he wanted to get
a better perspective on what exactly these services that companies make require to work.

I quickly decided that I'd show him Python first. It was a smart move. He instantly understood the way that print statements worked in Python and was hungry for more. Within an hour,
I had gotten through variables, operators, if/else statements, and for/while loops. And the thing is, he actually retained the information and was eager to learn the whole time.

I'm sure that had I shown him the same things in C# or Java, things would not have been quite so easy for him. It's crucial for a newbie to be able to understand exactly what is
happening in their program, without needing to tell them *"Don't worry about that yet"* or *"That's just how it has to be for now"*.

It's also important for a new programmer to be able to make things quickly, as it really helps to retain interest. When I had started taking classes for programming in 8th grade, 
it seemed that it took too much time and complexity to do simple things with Java. However, in Python, those same things are easier to understand and can be done much quicker (in many cases).

I don't want to act like Python is the superior language to Java. In many, many cases, Java is a far better language to use than Python. It has a lot more "real world" use cases, such as
in Android development or feasible GUI programs. I do believe, however, that there is a reason why Python is regarded as one of the best languages for beginners to start with.

So, what do you think is the best solution for the "Hello, World" program? I don't truly think the contents of the program matter (to an extent), but rather the language is 
what is important. Leave your opinion below!