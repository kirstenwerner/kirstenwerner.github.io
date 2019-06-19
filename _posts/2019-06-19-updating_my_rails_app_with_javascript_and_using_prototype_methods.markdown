---
layout: post
title:      "Updating my Rails app with JavaScript, and using prototype methods"
date:       2019-06-19 11:39:27 -0400
permalink:  updating_my_rails_app_with_javascript_and_using_prototype_methods
---


Here we are, at our fourth portfolio project of the course, and I have to admit that I was more scared going into this one than any of the previous projects. We had only studied JavaScript for three weeks at the point of beginning our projects, and it felt like we had covered so much material, I was nearly paralyzed at the idea of even narrowing down where to start! One of the things that was striking me as entirely mystifying was constructor and prototype functions - but after lots of digging (and some incredibly helpful chats with classmates), I've found that these are both quite simple. 

Let's start with talking about the constructor function. What would we use a constructor function for? One way that I came to understand the usefulness of the constructor function is to speed up processing time within my web app. I have to call to my database on the back when I want to use Javascript to display information stored within that database....but that takes processing time. Ideally I would make just ONE call to the database on the back end, and then store that information somewhere on the front end where I can reference it as many times as I like! This is where I can use a constructor method to store whatever information I want to assign to a new instance of my class within the classes object! 

For example: 
In my project app, I am able to create and store workouts, made up of individual skills. Each skill has a number of attributes, including name, description, target (muscle group or action that it works on), demo (video of how to do the skill properly). Using JavaScript, a user is able to click on any on of the skills to see a formated 'show' of the skills attributes. Once a skill is clicked, and the attributes shown once, I would like to have that information stored on my front end in order to speed up processing time each time the skill is clicked again within a session, rather that having to make a call back to my database on the back end every. single. time.  In order to accomplish this, I can use the JavaScript constructor function to format the information about the skill into an instance of my object right here on the front end, and access that so much faster! 

First, I defined an empty array in order to store all instances of skills that I make on the front end like so: 

 ```let allSkills = [ ]```

Next, I defined my class as Skill, and within that function call a constructor function with the attribute of the object I am working within, and within ~that~ function assigned the object properties to equal my new instance of the class' properties! Finally, I pushed the new instance of the class to my allSkills array, where I can access and reference any of the information stored there anywhere else I would like to, right on the front end. The resulting constructor function will look something like this: 

```class Skill {
    constructor(obj) {
      this.id = obj.id
      this.name = obj.name
      this.description = obj.description
      this.target = obj.target
      this.demo = obj.demo
      allSkills.push(this)
    }
  }```
	
Great, now I can create and store instances of my Skill class on the front end! Now what about when I want to act on those instances? This is where prototype methods functions come in....but what in the world is a prototype function?!  Simply put, every function in JavaScript has a prototype property that references an object. When I have an action that I I want to be able to take on any instance of my class object, I can write my function as a prototype, which allows it to become an internal function to the class, and called by linking via dot notation. 
	
I decided to use a prototype to format the html output for my skills show's, roughly like so:
	
```Skill.prototype.formatSkill = function(skill) {
   *html format code*
  }```
	
Then I am able to call that formatting prototype funtion later simply by:
	
```skillShow.innerHTML = skill.formatSkill(skill)```
	
Prototype is just a property that every function in JavaScript has and it allows us to share methods across all instances of a function!
	

