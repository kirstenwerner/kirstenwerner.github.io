---
layout: post
title:      "The most important thing to understand about Logic and Conditionals"
date:       2019-03-17 23:41:52 +0000
permalink:  the_most_important_thing_to_understand_about_logic_and_conditionals
---


As a newbie in coding, and the tech world in general, one of the most important - and most brain-numbingly difficult - things to wrap your head around is how to use Logic and Conditionals.

Each new functionality that you want to add to any code that you're writing, has to be worked through with logic that your computer will understand. While Ruby is a very syntacticly friendly language, it is still limited by needing to use Logic and Conditionals that are understood by developers and computers alike. 

For me, the most effective way to tackle any new logic problem is to break it down into the smallest steps possible. Instead of thinking of how to get from, say, the beginning of the alphabet to the end, you have to break it down into how to get from one letter to the next, until you reach your end goal. 

For example: If I want to take an array of integers, and double all of the odd numbers, how would I start?
array = [1, 3, 6, 15, 4, 2]

First off, I need to figure out how to tell if a number is odd. What do I know about odd numbers? Well, I know that they are not divisible by 2. Or in other words, would have a remainder if they were devided by 2.  So if int % 2 != 0, I know that its an odd number.  Good, thats a start. 

But then what? Well, I need to somehow go through the array to check each integer - hello loop!  I can iterate through my array with an each statement, and combine that with the my logic to see if each individual integer is odd, I will be somewhere near this: 

```
array.each do |integer|
   if integer % 2 != 0
	    # do something
	 end 
end
``` 

Finally, I'm left with just filling in what I want to actually accomplish! For each integer in the array, IF the integer is odd, I want to double it. So....

```
array.each do |integer|
   if integer % 2 != 0
	    integer * 2
	 end 
end
``` 

And wa-la! I've worked through the individual steps of logic and conditionals to reach my goal!

This step-by-step process can be used from the simplest to the most complex logic problems, and is the basis for all of the coding I have learned so far! 

